---
title: "You have an error in your SQL syntax; check the manual that corresponds to your MySQL"
date: 2009-08-30
forum: Server Platforms
---

### Post by habibiwalla on 2009-08-30
Hi All,

I have installed ubuntu 9 and downloaded mysql-server, JDBC connector and Eclipse 3.2 via synaptic Manager. The versions I have

mysql-server 5.1 (5.1.31 ubuntu 2)
mysqlclient 5.1 (5.1.31 ubuntu 2)
libmysql-java 5.1.6 JDBC (mysql-connector-java-5.1.6-bin.jar)
ubuntu 9

I was testing a simple code to check if a connection with a test database is established or not on mysql server but I keep receiving this error:

You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '????????????????' at line 1

I am using the username root and the password that I put during mysql installation. [COLOR=Red]The same code is working fine on my WIndows XP installation (mysql 5.1 and jdbc connector 5.1) with no errors.[/COLOR]

Why am I getting this problem ? I am not running any SQL query in the code!!!

Is there a version conflict with current ubuntu packages?

The whole code is listed below from a sun jdbc tutorial.


import java.sql.Connection;
import java.sql.DriverManager;

public class Connect {

public static void main(String args[]) {
Connection con = null;

try {
String username = "root";
String password = "pwd123";
String url = "jdbc:mysql://localhost:3306/mysql";
Class.forName("com.mysql.jdbc.Driver").newInstance  ();
con = DriverManager.getConnection(url, username, password);
System.out.println("Connection Established.");
}
catch(Exception e) {
System.err.println("Cannot Connect to DB. Exception: " + e.getMessage());
}

finally
{
if(con != null)
{
try
{
con.close();
}

catch(Exception e) {}
}
}
}
}

Thanks
                     
                                                                                                                                                                                                                                    [[IMG]http://www.dbforums.com/db_images_v3/images/buttons/edit.gif[/IMG]]("http://www.dbforums.com/editpost.php?do=editpost&p=6419333")

---

### Post by habibiwalla on 2009-08-31
com.mysql.jdbc.exceptions.MySQLSyntaxErrorException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '????????????????' at line 1
   at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:1026)
   at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:956)
   at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3491)
   at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3423)
   at com.mysql.jdbc.MysqlIO.sendCommand(MysqlIO.java:1936)
   at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:2060)
   at com.mysql.jdbc.ConnectionImpl.execSQL(ConnectionImpl.java:2536)
   at com.mysql.jdbc.ConnectionImpl.configureClientCharacterSet(ConnectionImpl.java:1751)
   at com.mysql.jdbc.ConnectionImpl.initializePropsFromServer(ConnectionImpl.java:3425)
   at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2045)
   at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:718)
   at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:298)
   at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:282)
   at java.sql.DriverManager.getConnection(libgcj.so.90)
   at java.sql.DriverManager.getConnection(libgcj.so.90)
   at Connect.main(Connect.java:14)

---

