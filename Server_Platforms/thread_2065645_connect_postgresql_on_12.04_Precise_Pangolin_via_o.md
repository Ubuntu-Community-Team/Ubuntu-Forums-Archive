---
title: "connect postgresql on 12.04 Precise Pangolin via odbc_fdw to MS SQL Server [Howto]"
date: 2012-10-02
forum: Server Platforms
---

### Post by Peter7707 on 2012-10-02
In case anybody wants to remote connect from postgresql to mssql server via odbc_fdw, here are some hints. There is no place on the internet where a working procedure is described for ubuntu 12.04 and in any case I thought it is useful to have it all together in one thread.

you should have postgresql9.1 already installed. 


A) to use odbc_fdw to connect to mssql, you need:
apt-get install unixodbc unixodbc-dev postgresql-server-dev.9.1 odbc-postgresql freetds-common freetds-dev tdsodbc freetds-bin sqsh

B) then download the source for odbc_fdw from [http://pgxn.org/dist/odbc_fdw/](http://pgxn.org/dist/odbc_fdw/) and unzip it
wget [http://api.pgxn.org/dist/odbc_fdw/0.1.0/odbc_fdw-0.1.0.zip](http://api.pgxn.org/dist/odbc_fdw/0.1.0/odbc_fdw-0.1.0.zip)
unzip odbc_fdw-0.1.0.zip (install unzip in case it is not installed)

C) clean, build and install according to [https://github.com/ZhengYang/odbc_fdw/#readme](https://github.com/ZhengYang/odbc_fdw/#readme). you have to change the path according to our postgresql location. in ubuntu 12.04 the path is /usr/lib/postgresql/9.1/bin/
1) first, clean compilation environment (according to [http://archives.postgresql.org/pgsql-general/2011-11/msg01142.php](http://archives.postgresql.org/pgsql-general/2011-11/msg01142.php))
PATH=/usr/local/pgsql/bin/:$PATH make USE_PGXS=1 clean
2) make
PATH=/usr/lib/postgresql/9.1/bin/:$PATH USE_PGXS=1 make
3) install
PATH=/usr/lib/postgresql/9.1/bin/:$PATH USE_PGXS=1 make install

D) create a ODBC entry. this is the trickiest part and took me some hours to find out what is wrong with the standard howtos.

you can follow this howto ([http://lambie.org/2008/02/28/connecting-to-an-mssql-database-from-ruby-on-ubuntu/](http://lambie.org/2008/02/28/connecting-to-an-mssql-database-from-ruby-on-ubuntu/)) but you have to alter the conf files as follows (don't add the comments after the #):

file /etc/freetds/freetds.conf
[mssql_freetds] #<-- this your TDS identifier
	host = your-mssql-server-ip
	port = 1433
	tds version = 7.0
	
file /etc/odbcinst.ini
[FreeTDS] #<-- TDS Driver name
Description = ODBC for Microsoft SQL
Driver = /usr/lib/x86_64-linux-gnu/odbc/libtdsodbc.so #<---use THIS PATH for ubuntu 12.04
Setup = /usr/lib/x86_64-linux-gnu/odbc/libtdsS.so #<---use THIS PATH for ubuntu 12.04
CPTimeout =
CPReuse = 
FileUsage = 1

file /etc/odbc.ini
[mssql_odbc] #<-- this your ODBC identifier
Driver = FreeTDS 
Description = ODBC Connection via FreeTDS
Trace = No
Servername = mssql_freetds #<--- NOT the mssql-server-ip but the TDS identifier used in the file /etc/freetds/freetds.conf!!
Database = your-database
UID = your-user
PWD = your-pass
Port = 1433
ReadOnly = No

first, make sure the connection with FreeTDS works (here you use the TDS identifier)
sqsh -S mssql_freetds -U your-user -P your-pass

if this works ok, then check out if the odbc connection works (here you use the odbc identifier)
isql -v mssql_odbc your-user your-pass 


E) now, in postgresql, create the extension for the odbc_fdw you compiled before. some useful howtos where I extracted the information:
[http://www.postgresonline.com/journal/archives/249-ODBC-Foreign-Data-wrapper-to-query-SQL-Server-on-Window---Part-2.html](http://www.postgresonline.com/journal/archives/249-ODBC-Foreign-Data-wrapper-to-query-SQL-Server-on-Window---Part-2.html)
[http://wiki.hsr.ch/Datenbanken/files/SQLMED_and_More_Schwendener_Presentation.pdf](http://wiki.hsr.ch/Datenbanken/files/SQLMED_and_More_Schwendener_Presentation.pdf)
[http://brunosimioni.wordpress.com/](http://brunosimioni.wordpress.com/)

1) CREATE extension odbc_fdw; 
eventually create extra schema for remote tables: CREATE schema mssql_schema;
2) create server connection
CREATE SERVER mssql_remote FOREIGN DATA WRAPPER odbc_fdw OPTIONS (dsn 'mssql_odbc'); #<-- USE ODBC identifier you created in /etc/odbc.ini!
CREATE USER MAPPING FOR postgres SERVER mssql_remote OPTIONS (username 'your-user', password 'your-pass');

adapt the following sql to your tables:
CREATE FOREIGN TABLE mssql_remote.local_table (
	local_id integer, 
	local_name varchar(255)
)
SERVER mssql_remote
OPTIONS (
 database 'your-database',
 schema 'dbo',
 table 'remote_table',
 sql_query 'SELECT id,name FROM remote_table',
 sql_count 'SELECT COUNT(id) FROM remote_table',
 local_id 'id',
 local_name 'name');

I did not succeed if I didn't add the individual columns in the options of the CREATE FOREIGN TABLE statement (local_id 'id', local_name 'name') although they are optional.
 
3) query the foreign table: 
 SELECT * FROM mssql_schema.local_table;


if you want to drop the foreign server, do either a cascade drop to drop everything:
DROP SERVER mssql_remote CASCADE;
or drop the table and user mappings individually:
DROP USER MAPPING FOR postgres SERVER mssql_remote;
DROP FOREIGN table local_table;

---

### Post by MyKillK on 2012-10-31
Wonderful post, helped me so so much!

There is one correction that needs to be made:

You advise in Step E to do CREATE FOREIGN TABLE mssql_remote.local_table (
    local_id integer, 
    local_name varchar(255)
)...

Looks like you mixed up the server and the schema. It should be CREATE FOREIGN TABLE mssql_schema.local_table ...

I also was not able to drop my foreign table without specifying the schema so DROP FOREIGN table local_table should read DROP FOREIGN table mssql_schema.local_table

Thanks so much for this post!

Ubuntu 12.04 / PostgreSQL 9.1 / MS SQL Server 2008

---

### Post by MyKillK on 2012-10-31
I also have a question for you, or anyone else for that matter.

The only way I can access the data from the MSSQL DB is to execute a SQL query. In my PgAdminIII, no tables show up under the mssql schema, even though, like I said, I can access the table with a query.

Is there any way the MS SQL tables can show up, preferably automatically, as a table under the mssql_schema?

---

### Post by Peter7707 on 2012-11-06
Dear MyKillK,

thank you for you corrections.

regarding your question: I also don't see the foreign tables in pgadmin, I only can query them with executing a SQL query. But when using the remote tables with functions this doesn't matter too much.

Because the remote connection was primarily a test for a future upgrade of our database (which didn't happen so far and won't in the coming months), I didn't follow the topic any more since posting for the first time.

It would in any case be handy to also see the tables in pgadmin. If you find out how, please post it here. 

In the information schema (<DB/>/Catalogs/ANSI (Information schema)/Catalog Objects/foreign_tables and foreign_servers) you have the information which tables are referenced via odbc_fdw. 

Peter

---

