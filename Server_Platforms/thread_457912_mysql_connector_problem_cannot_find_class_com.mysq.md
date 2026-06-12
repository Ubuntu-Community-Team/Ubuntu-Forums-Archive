---
title: "mysql connector problem cannot find class com.mysql.jdbc.Driver"
date: 2007-05-29
forum: Server Platforms
---

### Post by kanna1620 on 2007-05-29
Hi all!
I am using Ubuntu 7.04. I installed mysql5.0. I wrote a java program to connect to the mysql database. The code is:
> import java.sql.*;
//import java.util.Properties;

public class DBconnect
{
	// The JDBC Connector Class.
	 private static final String driver = "com.mysql.jdbc.Driver";
	//
	// // Connection string. db2007 is the database the program
	// // is connecting to. You can include user and password after this
	// // by adding (say) ?user=paulr&password=paulr. Not recommended!
	//
	 private static final String url = "jdbc:mysql://localhost/db2007";
	
	 public static void main(String[] args) throws ClassNotFoundException,SQLException
	 {
		 System.out.println(driver);
		 try
		 {
			 Class.forName(driver);
 			 Connection c = DriverManager.getConnection(url,"xxxx","xxxx");
 			 c.close();
		 	 System.out.println("It works !");
 		 }
 		 catch(Exception e)
 		 {
 			 e.printStackTrace();
 		 }
	 }
}
But the database cannot be accessed as it is giving the following error:

> com.mysql.jdbc.Driver
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at DBconnect.main(DBconnect.java:20)

Please some body help me out to get connection with my database. I tried many threads but with no success. Please some body help me. :(

---

### Post by craigp84 on 2007-05-29
Hi kanna1620,

Your classpath is wrong. Ensure your classpath includes the MySQL connector .jar file.

This is not a "Servers & Security" problem, nor even an Ubuntu issue, please post this type of issue in a Java or MySQL forum in future.

Thanks,

Craig

---

### Post by bedjo on 2007-07-11
if you are using netbeans IDE, try this

[http://www.netbeans.org/kb/41/using-netbeans/project_setup.html#manageclasspath](http://www.netbeans.org/kb/41/using-netbeans/project_setup.html#manageclasspath)

---

