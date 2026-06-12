---
title: "mySQL not returning data"
date: 2011-10-02
forum: Server Platforms
---

### Post by Rebajas on 2011-10-02
Hiya,

I have a 'platform' that I have been using without problem for several years on various past computers running Ubuntu, PHP, mySQL & Apache.

Last week I decided that rather than having to keep moving the setup from computer to computer as time progresses I'd just put it all on my Ubuntu Server based server.

All went well until I tried running my sites, I get the following errors:

```
Warning: mysql_fetch_row() expects parameter 1 to be resource, boolean given in /sites/platforms/init.php on line 14
```

```
Warning: mysql_num_rows() expects parameter 1 to be resource, boolean given in /sites/platforms/main.php on line 91
```

Usually I'd assume this was a error in the SQL but it has been and still is running fine in various other places, so I conclude there is something that needs changing in my new setups config, any ideas?

Thanks in advance, and if you need further info let me know and I will try and provide

---

### Post by SeijiSensei on 2011-10-02
The errors indicate that the PHP mysql client cannot connect to the database.  Possible reasons include:

1)  The mysql server isn't running, or it's not configured to house the database you're looking for.  Try running "sudo service mysql restart" to make sure the server is up.

Also you should try connecting with the [mysql client]("http://dev.mysql.com/doc/refman/5.5/en/programs-client.html") from the terminal prompt.  Run "sudo apt-get install mysql-client" first to make sure you have the client installed.

2)  You have misconfigured the PHP [mysql_connect()]("http://php.net/manual/en/function.mysql-connect.php") function.

More help [here](https://help.ubuntu.com/community/ApacheMySQLPHP).

The other possibility is that MySQL is running, but you didn't build the data base it's looking for.  Did you import the data from another installation using mysqldump?

---

### Post by Rebajas on 2011-10-02
Hi SeijiSensei, thanks for replying.

I ran sudo service mysql restart and the service restarted; I knew the service was running though as I have connected to the database via terminal frequently.

I ran "sudo apt-get install mysql-client" just to check that was installed, it wasn't so I let that continue then restarted the mysql service again but still no connection.

I have built the database using mysqldump from a working server with more or less the same configuration, I guess something somewhere is just different enough to stop it all working :)

I'll have a look around the php.ini and see if I can see anything different from the other machine; thankfully they are both right in front of me!

---

### Post by Rebajas on 2011-10-02
I've been through my php.ini line for line and can see no differences, any other ideas?


Thanks in advance.

---

### Post by SeijiSensei on 2011-10-02
> **Rebajas said:**
> I've been through my php.ini line for line and can see no differences, any other ideas?

php.ini isn't the issue.  What does the mysql_connect() statement in the application itself look like?  What do the mysql_query() and mysql_num_rows() statements in the code that throw the errors look like?

Now that mysql-client is installed, what happens when you run

```
mysql -u username databasename
```

I'm also a bit puzzled as to how you could port over the database with mysqldump if you didn't have mysql-client installed.  Usually you run something like:

```
mysql -u root -p password < yourdumpfile
```

to rebuild the database.

---

### Post by Rebajas on 2011-10-02
Well I had mysql-server installed, maybe that's enough for mysqldump to work?

Anyway, as to you points about the code, the code works elsewhere. All on Ubuntu, on both desktop and headless server, all set up from scratch by myself with no issues. It's perplexing to say the least!

The code looks like this:

```
function mySqlConnect($sql) {

        $hostname = "localhost";
        $username = "root";
        $password = "password";
        $database = "database_name";

        $mySqlConnect = mysql_connect($hostname, $username, $password);
        mysql_select_db($database, $mySqlConnect);
        $results = mysql_query($sql);

        return $results;

}
```

Then the other end of that looks like this:

```
$sql = "SELECT table1.contentID, table1.navigationID, table1.header, table1.body, table1.styles, table2.title, table2.description, table2.keywords ";
$sql .= "FROM table1, table2 ";
$sql .= "WHERE (table1.siteID = '".$init_siteID."') ";
$sql .= "AND (table1.contentID = table2.contentID) ";
$sql .= "AND (table1.routing = '".$init_routing."') ";
$sql .= "LIMIT 1;";
$results = mySqlConnect($sql);
$contentData = mysql_fetch_row($results);
```

I think that is pretty stable as I have been using that exact setup for years with no problem.

logging into mySQL with "mysql -u username -p database" has worked the entire time; once again I don't know if you need mysql-client for that. If you do, then maybe it was installed all the time and I just misread the response from Aptitude?

Anyway, I do appreciate your help - I'm wondering if I should do a rebuild from scratch, I've built this set up about 6 times with no problem so wondering if I just have a duff install?


Tony.

---

