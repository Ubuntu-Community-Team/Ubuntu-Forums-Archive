---
title: "Problem in migrate tables MySQL to DB2 with IBM Migration ToolKit"
date: 2013-10-03
forum: Server Platforms
---

### Post by tylervortexbr on 2013-10-03
Hello to all.


I intend to migrate MySQL database to DB2 by company policy but I am experiencing several problems with the tool IBM Migration Toolkit.


The driver stated that db2jcc_license_cu.jar was not loaded, and had already informed in this jar path.


Would you like some help or know a way to migrate at least 200 MySQL to DB2 tables so quickly and effectively.


Look see please:

[IMG]http://i75.servimg.com/u/f75/11/80/81/44/print_10.jpg[/IMG]




Thank you in advance to all.

---

### Post by SeijiSensei on 2013-10-03
Do you have a copy of Microsoft Access available?  You could connect to both the MySQL and DB2 servers using ODBC and move the tables between the servers that way.

---

### Post by Habitual on 2013-10-03
It says "Please connect to DB2 first", did you? 

["MTK must not be installed into a directory with a space in the name"]("https://www-304.ibm.com/support/docview.wss?uid=swg27009230#freq_quest__whatdbmigrate")
/home/daysoft/Documents/tools IBM/
appears to have a space in it.

It's hard to tell what may be needed from just a sole screen capture.

---

### Post by tylervortexbr on 2013-10-04
> **Habitual said:**
> It says "Please connect to DB2 first", did you? 

["MTK must not be installed into a directory with a space in the name"]("https://www-304.ibm.com/support/docview.wss?uid=swg27009230#freq_quest__whatdbmigrate")
/home/daysoft/Documents/tools IBM/
appears to have a space in it.

It's hard to tell what may be needed from just a sole screen capture.


Hello,
I appreciate the tip, I renamed the directory correctly.


Changed the tool I am now using IBM Migration Toolkit, it seems to work a little better.
I have a big sql file, but contains simple lines like:

```
-- CREATE DATABASE  IF NOT EXISTS `h_camprev` /*!40100 DEFAULT CHARACTER SET latin1 COLLATE latin1_general_ci */;
-- USE `h_camprev`;
-- MySQL dump 10.13  Distrib 5.6.11, for Win32 (x86)
--
-- Host: 186.234.192.102    Database: h_camprev
-- ------------------------------------------------------
-- Server version       5.5.29-log


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


--
-- Table structure for table `AuthAssignment`
--


DROP TABLE IF EXISTS `AuthAssignment`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `AuthAssignment` (
  `itemname` varchar(64) NOT NULL,
  `userid` varchar(64) NOT NULL,
  `bizrule` text,
  `data` text,
  PRIMARY KEY (`itemname`,`userid`),
  KEY `idx_user_id` (`userid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

```


I have some prints of each process step.
Also post the logs tool initialized by terminal linux.

[http://i75.servimg.com/u/f75/11/80/81/44/print_10.png](http://i75.servimg.com/u/f75/11/80/81/44/print_10.png)

[http://i75.servimg.com/u/f75/11/80/81/44/print_11.png](http://i75.servimg.com/u/f75/11/80/81/44/print_11.png)

[http://i75.servimg.com/u/f75/11/80/81/44/print_12.png](http://i75.servimg.com/u/f75/11/80/81/44/print_12.png)



So far the file hcampre.db2 is empty.

```
 --* [300000]MTK MySQL Converter.  Version: 03Jun2010_1055

"hcampre.db2" 2L, 59C 

```


I even renaming generates an exception name directory, I believe.

```
VirtualBox:~/DB2MigrationToolKit$ sh MTKMain.sh 
Fri Oct 04 07:24:27 EDT 2013    INFO    MTK    Version 2.0.5.1, build: 03Jun2010_1055
Fri Oct 04 07:26:18 EDT 2013    INFO    DBTREEMODEL    Loading DB Tree
Fri Oct 04 07:26:18 EDT 2013    INFO    DBTreeExtension    Loading DB Tree. Use XMI file = true
Fri Oct 04 07:36:42 EDT 2013    INFO    TranslationExtensionMySQL    Adding notranslate file /home/daysoft/DB2MigrationToolKit/projects/hcampre/hcampre.prg
Fri Oct 04 07:36:43 EDT 2013    INFO    TranslationExtensionMySQL    Adding file /home/daysoft/DB2MigrationToolKit/projects/hcampre/hcampre.sql
Fri Oct 04 07:36:43 EDT 2013    INFO    TranslationExtensionMySQL    Translation starting: options:atomicSource=true, topLevelSource=true, comments=true, nopad=false, dropddl=false, dropdml=false, genReportFile=true, genXmiFile=true, nosource=false, prt_src_if_err=false, statementTerminator=!, outputDir=/home/daysoft/DB2MigrationToolKit/projects/hcampre, outputFilename=hcampre
Fri Oct 04 07:36:44 EDT 2013    INFO    DBTREEMODEL    Loading DB Tree
Fri Oct 04 07:36:44 EDT 2013    INFO    DBTreeExtension    Loading DB Tree. Use XMI file = false
Fri Oct 04 07:36:45 EDT 2013    INFO    REPORTS_GENERATOR    MTKReportsGenerator at 451 = /home/daysoft/DB2MigrationToolKit/projects/hcampre/Reports/Conversion_hcampre.html
Exception in thread "Thread-7" java.lang.OutOfMemoryError: Java heap space
    at java.util.Arrays.copyOf(Arrays.java:2367)
    at java.lang.String.<init>(String.java:168)
    at com.ibm.mtk.translation.util.InputFileInfo.getBuffer(InputFileInfo.java:76)
    at com.ibm.mtk.translation.source.common.Translator.convert(Translator.java:347)
    at com.ibm.mtk.model.translation.MTKTranslationExtensionMySQL.translateExecute(MTKTranslationExtensionMySQL.java:294)
    at com.ibm.mtk.model.translation.MTKTranslationModelElement.translate(MTKTranslationModelElement.java:307)
    at com.ibm.mtk.ui.translator.MTKTranslatorView$14.run(MTKTranslatorView.java:1389)


```


I hope I have detailed enough.
Thank you in advance.

---

### Post by Habitual on 2013-10-04
The error is "java.lang.OutOfMemoryError: Java heap space"
documents suggest starting the jvm with this or a similar switch:
[FONT=courier new]java -Xmx1024m ...
This will allocate 1G of memory to the program called after that switch on [the command-line]("http://www.ibm.com/developerworks/data/library/techarticle/dm-0707adio/").
adjust up **if** you have the memory, [/FONT][FONT=courier new]How much memory do you have?[/FONT][FONT=courier new]
How that's done using MTK, I do not know, sorry. Perhaps the above link can help, or the [FAQ]("https://www-304.ibm.com/support/docview.wss?uid=swg27009230") ?

Sorry, I wish I knew more.
[/FONT]

---

### Post by tylervortexbr on 2013-10-04
I wonder if you already used the previous tool in which I was struggling.


Follow this tutorial to install libmysql-java / usr / share / java:
[https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)


I do not know if the problem was setup for IBM DB2 JDBC, but whatever it is, is something.


Already tool IBM Migration Toolkit, it converts files in DB2 after it gives me the opportunity to do a "deploy" with the generated files, but this never worked well.


* For the VM I increased the memory 1Gb (specified for DB2) to 3Gb, so hopefully the tool hang because my computer crashed when I was with 1Gb.


I hope you have specified a little more the problem.

---

### Post by tylervortexbr on 2013-10-07
Hello to all!
Running DB2 Migration ToolKit I realized that the JDBC driver for IBM DB2 is not started or informed.


I would like to know how to fix it, because I did a connection for a java class that I created for these tests and connected successfully.


How to report this to the tool?
Already realized the export = $ CLASSPATH with the files and jars mysql.jar java_uno.jar and db2jcc.jar.

```

~/DB2MigrationToolKit$ ./MTKMain.sh 
Mon Oct 07 08:38:55 EDT 2013	INFO	MTK	Version 2.0.5.1, build: 03Jun2010_1055
Mon Oct 07 08:39:04 EDT 2013	INFO	DBTREEMODEL	Loading DB Tree
Mon Oct 07 08:39:04 EDT 2013	INFO	DBTreeExtension	Loading DB Tree. Use XMI file = true
Mon Oct 07 08:39:17 EDT 2013	INFO	ConnectDialog	DBName: MySQL connected
Mon Oct 07 08:39:17 EDT 2013	INFO	ConnectDialog	DBName: MySQL connected
Mon Oct 07 08:39:17 EDT 2013	INFO	MYSQLEXTCAT	time to read database list = 18
Mon Oct 07 08:39:58 EDT 2013	INFO	WIZARD: WIZARDMODEL	DBName: MySQL connected
Mon Oct 07 08:39:58 EDT 2013	INFO	EXTRACTME	Extraction started
Mon Oct 07 08:40:00 EDT 2013	INFO	MYSQLEXTCAT	time to write source for selected objects = 1949
Mon Oct 07 08:40:00 EDT 2013	INFO	EXTRACTME	Extraction completed
Mon Oct 07 08:40:00 EDT 2013	INFO	TranslationExtensionMySQL	Adding notranslate file /home/daysoft/DB2MigrationToolKit/projects/hcamprev/mtkWizard.prg
Mon Oct 07 08:40:00 EDT 2013	INFO	TranslationExtensionMySQL	Adding file /home/daysoft/DB2MigrationToolKit/projects/hcamprev/WizardExtractorOutput.src
Mon Oct 07 08:40:00 EDT 2013	INFO	TranslationExtensionMySQL	Translation starting: options:atomicSource=true, topLevelSource=true, comments=true, nopad=false, dropddl=false, dropdml=false, genReportFile=true, genXmiFile=true, nosource=false, prt_src_if_err=false, statementTerminator=!, outputDir=/home/daysoft/DB2MigrationToolKit/projects/hcamprev, outputFilename=mtkWizard
Mon Oct 07 08:40:02 EDT 2013	INFO	TRANSLATIONME	Translation completed successfully
Mon Oct 07 08:40:02 EDT 2013	INFO	DBTREEMODEL	Loading DB Tree
Mon Oct 07 08:40:02 EDT 2013	INFO	DBTreeExtension	Loading DB Tree. Use XMI file = false
Mon Oct 07 08:40:03 EDT 2013	INFO	DBTREEMODEL	DB Tree Loaded
Mon Oct 07 08:40:03 EDT 2013	INFO	TRANSLATIONME	start buildReports: Memory Total=65994752, Free:51451568
Mon Oct 07 08:40:03 EDT 2013	INFO	TRANSLATIONME	rootName=mtkWizard
Mon Oct 07 08:40:04 EDT 2013	INFO	WIZARD: WIZARDMODEL	DBName: MySQL connected
Mon Oct 07 08:40:04 EDT 2013	INFO	DATAMOVEMENTME	Script generation started
Mon Oct 07 08:40:05 EDT 2013	INFO	DATAMOVEMENTME	Script generation done
Mon Oct 07 08:40:05 EDT 2013	INFO	DeploymentExtensionUNO	Running scripts started
Mon Oct 07 08:40:05 EDT 2013	INFO	DeploymentExtensionUNO	Adding MTK UDFs and JAR to deployment script
Mon Oct 07 08:40:05 EDT 2013	INFO	DeploymentExtensionUNO	The creation of the script file (/home/daysoft/DB2MigrationToolKit/projects/hcamprev/Deploy_mtkWizard.sh) succeeded
Mon Oct 07 08:40:05 EDT 2013	INFO	DEPLOYMENTMODEL	Number of error messages in DB2 file:
Mon Oct 07 08:40:05 EDT 2013	INFO	DEPLOYMENTMODEL	* * 4 Messages of category Input Script Error [20xxxx]
Mon Oct 07 08:40:05 EDT 2013	INFO	DEPLOYMENTMODEL	* * 328 Messages of category Translator Warning [60xxxx]
com.ibm.db2.jcc.am.SqlException: [jcc][10389][12245][3.66.46] Failure in loading native library db2jcct2, java.lang.UnsatisfiedLinkError: no db2jcct2 in java.library.path:  ERRORCODE=-4472, SQLSTATE=null
	at com.ibm.db2.jcc.am.dd.a(dd.java:725)
	at com.ibm.db2.jcc.am.dd.a(dd.java:60)
	at com.ibm.db2.jcc.am.dd.a(dd.java:94)
	at com.ibm.db2.jcc.t2.a.a(a.java:37)
	at com.ibm.db2.jcc.t2.T2Configuration.<clinit>(T2Configuration.java:95)
	at com.ibm.db2.jcc.DB2Driver.connect(DB2Driver.java:435)
	at com.ibm.db2.jcc.DB2Driver.connect(DB2Driver.java:115)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:200)
	at com.ibm.mtk.util.MTKDB2Connection.open(MTKDB2Connection.java:101)
	at com.ibm.mtk.util.MTKDB2Connection.open(MTKDB2Connection.java:73)
	at com.ibm.mtk.model.deployment.MTKDeploymentExtensionUNO.upgradeDB(MTKDeploymentExtensionUNO.java:579)
	at com.ibm.mtk.model.deployment.MTKDeploymentModelElement.deploy(MTKDeploymentModelElement.java:798)
	at com.ibm.mtk.wizard.MTKWizardModel.startTargetDatabase(MTKWizardModel.java:913)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun.startTargetDB(MTKWizardTaskToRun.java:343)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun.access$600(MTKWizardTaskToRun.java:30)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun$ActualTask.<init>(MTKWizardTaskToRun.java:201)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun$1.construct(MTKWizardTaskToRun.java:172)
	at com.ibm.mtk.util.SwingWorker$2.run(SwingWorker.java:128)
	at java.lang.Thread.run(Thread.java:679)
com.ibm.db2.jcc.am.SqlException: [jcc][10389][12245][3.66.46] Failure in loading native library db2jcct2, java.lang.UnsatisfiedLinkError: no db2jcct2 in java.library.path:  ERRORCODE=-4472, SQLSTATE=null
	at com.ibm.db2.jcc.am.dd.a(dd.java:725)
	at com.ibm.db2.jcc.am.dd.a(dd.java:60)
	at com.ibm.db2.jcc.am.dd.a(dd.java:94)
	at com.ibm.db2.jcc.t2.a.a(a.java:37)
	at com.ibm.db2.jcc.t2.T2Configuration.<clinit>(T2Configuration.java:95)
	at com.ibm.db2.jcc.DB2Driver.connect(DB2Driver.java:435)
	at com.ibm.db2.jcc.DB2Driver.connect(DB2Driver.java:115)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:200)
	at com.ibm.mtk.util.MTKDB2Connection.open(MTKDB2Connection.java:101)
	at com.ibm.mtk.util.MTKDB2Connection.open(MTKDB2Connection.java:73)
	at com.ibm.mtk.model.deployment.MTKDeploymentExtensionUNO.upgradeDB(MTKDeploymentExtensionUNO.java:579)
	at com.ibm.mtk.model.deployment.MTKDeploymentModelElement.deploy(MTKDeploymentModelElement.java:798)
	at com.ibm.mtk.wizard.MTKWizardModel.startTargetDatabase(MTKWizardModel.java:913)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun.startTargetDB(MTKWizardTaskToRun.java:343)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun.access$600(MTKWizardTaskToRun.java:30)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun$ActualTask.<init>(MTKWizardTaskToRun.java:201)
	at com.ibm.mtk.wizard.MTKWizardTaskToRun$1.construct(MTKWizardTaskToRun.java:172)
	at com.ibm.mtk.util.SwingWorker$2.run(SwingWorker.java:128)
	at java.lang.Thread.run(Thread.java:679)
Mon Oct 07 08:40:05 EDT 2013	ERROR	DeploymentExtensionUNO	The DB2 Connection to the database HCAMPREV failed (rc=-6) with the following error message:[jcc][10389][12245][3.66.46] Failure in loading native library db2jcct2, java.lang.UnsatisfiedLinkError: no db2jcct2 in java.library.path:  ERRORCODE=-4472, SQLSTATE=null
Mon Oct 07 08:40:05 EDT 2013	ERROR	VERIFICATION	The connection to the DB2 database HCAMPREV failed.
Mon Oct 07 08:40:05 EDT 2013	ERROR	VERIFICATION	[jcc][10389][12245][3.66.46] Failure in loading native library db2jcct2, java.lang.UnsatisfiedLinkError: no db2jcct2 in java.library.path:  ERRORCODE=-4472, SQLSTATE=null
Mon Oct 07 08:40:05 EDT 2013	INFO	DEPLOYMENTMODEL	Deployment completed. rc=-6


```


[COLOR=#000000]I hope you have specified a little more the problem.[/COLOR]

---

