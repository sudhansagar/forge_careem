 Database Design
 ----------------
 
 Create tables as below for the requirement
 
 1)CUSTOMER
 
 --------------
 Column Name            Column Type           
 --------------------------------------------
 CUSTOMER_ID            BIGINT  -- pk
 CUSTOMER_NAME          VARCHAR(30)
 MOBILE_NO              VARCHAR(12)
 EMAIL                  VARCHAR(20)
 CREATE_DATE            TIMESTAMP
 UPDATE_DATE            TIMESTAMP
 
 2)VEHICLE
 -----------
  Column Name            Column Type           
 --------------------------------------------
  VEHICLE_NO             VARCHAR(20) -- pk
  VEHICLE_TYPE           VARCHAR(20)
  VEHICLE_NAME           VARCHAR(20)
  CREATE_DATE            TIMESTAMP
  UPDATE_DATE            TIMESTAMP
  
 3)DRIVER
 -----------
   Column Name            Column Type           
 --------------------------------------------
    DL_NO                 VARCHAR(20) --pk
    D_NAME                 VARCHAR(30)
    MOBILE_NO              VARCHAR(12)
    ADDRESS                VARCHAR(30)
    UID(ANY ID)            VARCHAR(16)
    VEHICLE_NO            VARCHAR(20)  -- fk ON VEHICLE_NO OF VEHICLE TABLE
    CREATE_DATE           TIMESTAMP
    UPDATE_DATE            TIMESTAMP
  
 4)RIDES
 ----------
   Column Name            Column Type           
 --------------------------------------------
   RIDES_ID               BIGINT
   CUSTOMER_NAME          VARCHAR(30)
   DRIVER_NAME            VARCHAR(30)
   FROM_LOACTION          VARCHAR(50)
   TO_LOCATION            VARCHAR(50)
   RIDE_STATUS            VARCHAR(20)
   BOOKING_DATE           TIMESTAMP
   RIDE_DATE              TIMESTAMP
   
5)CUSTOMER_FEEDBACK
 ---------------------
   Column Name            Column Type           
 --------------------------------------------
  CUSTOMER_ID              BIGINT
  DL_NO                    VARCHAR(30)
  MESSAGE                  VARCHAR(100)
  RATING                   VARCHAR(1)
  
 

  -------------------------
  Technology and Tools 
  ------------------------
  
  - RESTfull services(Jersey)
  - Spring Data JPA
  - Google APIs
  - Apache Maven
  - MySql
  - HA Proxy
  - JBoss Application Server
  -Message Broker (JMS/RabbitMQ/ActiveMQ)
  
   Cron Jobs
  ----------
 A cron Jobs keeps running to fetch gps points from drivers move while in a job and store in the DB. 


 Google Map API will be implementation
  1. Distance Matrix
    API URL : https://developers.google.com/maps/documentation/distance-matrix/intro
    DESC : Distance will be calculated between the customer and drivers, by using this we should be able to decide which driver is near by to the customer
  Direction 
    API URL : https://developers.google.com/maps/documentation/directions/intro 
    DESC : Direction will me mapped on map between customer and driver


 Load balancer
   HA Proxy will be configured in the system which acts as a host communcating with jboss nodes 

 JBoss multiple nodes will be created 

 Algorithm to dispatch the job to driver will on the basis of 
	----------------------------------------------------------------------------------
	Ratings for that driver. 
	Probability of the driver cancelled the job.
	Probability of the driver starts from receiving the job. 
	Driver drives over speed and rash drive. 


