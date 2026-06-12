---
title: "Setup PostgreSQL Webserver?"
date: 2005-12-04
forum: Server Platforms
---

### Post by fsgpr on 2005-12-04
I am trying to setup a machine with PostgreSQL as a webserver (for now just to learn from).  

I have a simple example database setup setup using psql.  I have Apache Server installed.

What are the basic steps to make it so I can view/edit the database through a web browser?  (just a trivial example would be great for now, such as view a table and do an Insert command if that makes it easier).

Any advice would be appreciated.  Thanks.

Edit:  PGP was also setup too...  I think there is probably something simple (I am new to Linux, Apache, PHP, and PostgreSQL, but have to start somewhere so thanks for your understanding..)

I found a reference to a function pg_connect()  which seems to be what I need to use, but get an error that it is an undefined function, maybe an additional package needs to be installed?

For completeness here is the code I have so far (adapted from [http://www.onlamp.com/pub/a/onlamp/2002/01/24/postgresql.html):](http://www.onlamp.com/pub/a/onlamp/2002/01/24/postgresql.html):)

<?
  // make our connection
  $connection = pg_connect("dbname=mydb user=fsgpr");
  // let me know if the connection fails
  if (!$connection) {
    print("Connection Failed.");
    exit;
  }
  // declare my query and execute
  $myresult = pg_exec($connection, "SELECT * FROM memberdetails");
  // process results
  for ($lt = 0; $lt < pg_numrows($myresult); $lt++) {
    $state = pg_result($myresult, $lt, 0);
    $zipcode = pg_result($myresult, $lt, 1);
    $email = pg_result($myresult, $lt, 2);
    $date = pg_result($myresult, $lt, 3);
    // print results
    print("State: $state<br />\n");
    print("Zipcode: $zipcode<br />\n");
    print("First Name: $email<br />\n");
    print("Last Name: $date<br />\n");
  }
?>

---

### Post by fsgpr on 2005-12-05
NM on this, all I needed to do was reboot (some service had to get reset I am sure).  Thanks though.

---

### Post by dudus on 2005-12-05
There is a module needed to connect php to psql. It's supposed to be installed by default in this ubuntu configuration.

To perform operation in the db you use a languae called sql. All the databases uses the same language. But each one has it's owns distinctions. But they follow the same logic. 

The best place to learn about pgsql is of course their site: 
[http://www.postgresql.org]("http://www.postgresql.org")

Try [their tutorial]("http://www.postgresql.org/docs/8.1/interactive/tutorial.html") as a start

---

### Post by fsgpr on 2005-12-05
Thanks for the reply, I have it working to the point where I can practice now, it really was not anywhere near as hard to get going as I feared (I just needed to reboot after installing one of the packages).

One general question I have though.  I have been using a text editor to type my SQL code into a file and then have been pasting it into PSQL.  Is this the normal way it is done or am I missing something.

---

