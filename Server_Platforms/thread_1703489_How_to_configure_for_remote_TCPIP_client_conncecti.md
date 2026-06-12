---
title: "How to configure for remote TCP/IP client conncections using MS Visual Basic OLE DB c"
date: 2011-03-09
forum: Server Platforms
---

### Post by JohnInNacogdoches on 2011-03-09
Hey guys, I'm trying to get a VB program to make a client connection to my PostgreSQL server running on an Ubuntu 10.10 server.

Here's what I've done:

Client side - installed and registered the OLE DB .dll's from the PostgreSQL OLE DB Provider project.

server side - 

the configuration described here: [https://help.ubuntu.com/10.10/serverguide/C/postgresql.html](https://help.ubuntu.com/10.10/serverguide/C/postgresql.html)

---------------
Have added this line to postgresql.conf:


listen_addresses = '*, 144.96.80.35, localhost'

I've also tried this as simply:

listen_addresses = '144.96.80.35, localhost'

also, port = 5432

--------------

I have added the following to pg_hba.conf:


# IPv4 local connections:
host    all         all         144.96.80.35  255.255.255.0         md5
local   all     postgres        md5


--------------

I've got the following code going in VB:

Public Class Form1

    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load
        Const connString As String = "Provider=PostgreSQL; Server=144.96.80.35; User Id=postgres;Password=postgres;"

        Dim theOleDBconnection As New OleDb.OleDbConnection

        theOleDBconnection.ConnectionString = connString


        theOleDBconnection.Open()
    End Sub
End Class

So when the project opens up, it should make the connection and display the form.

What happens is that I get an error...

OleDbException was unhandled

could not connect to server: Connection refused (0x0000274D/10061)
    Is the server running on host "" and accepting
    TCP/IP connections on port 5432?

---------------------------

So, obviously I've got something configured incorrectly.

I'm troubled that the VB error seems to show a null value for the host. Shouldn't that be the Server value in the connection string?

Thanks to all for any help?

---

### Post by dtfinch on 2011-03-09
Can you connect to the server from other programs like pgAdmin?

---

### Post by JohnInNacogdoches on 2011-03-09
Not sure - doesn't look like...but it seems to see that there is a server there.

I've put pgAdmin III on my client computer and done a

File -> Add Server command

entered the ip address of the server machine and used the postgres userID and password - have also tried it without the password hoping for a prompt, no luck...

I get a short 'Connecting to database... Done.' message but the server does not seem to be added to the Object Browser or the Server Groups. I don't see any object that probably should be there...

Thing is that when I five a host IP address that I know does not have a PostgreSQL server, I get a message saying "Server doesn't listen"

---

### Post by doas777 on 2011-03-09
well, first thing I woudl do is test connectivity with the server.
on the server side, is port 5432 open? you can view open ports with 
```
sudo netstat -ntlup
```

I assume based on your IP address, that you are connecting over the internet. do you have a stateful packetfilter/firewall in place between you and the server?

if you have a gui on the server, you can go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to test that the port is visible to the outside world. 

if those conditions are met, then the postgre config is the issue.

---

### Post by JohnInNacogdoches on 2011-03-09
> **doas777 said:**
> well, first thing I woudl do is test connectivity with the server.
on the server side, is port 5432 open? you can view open ports with 
```
sudo netstat -ntlup
```I assume based on your IP address, that you are connecting over the internet. do you have a stateful packetfilter/firewall in place between you and the server?

if you have a gui on the server, you can go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to test that the port is visible to the outside world. 

if those conditions are met, then the postgre config is the issue.

I'm on the same network segment as the server, so no firewall between us.

Turns out there was a postgre configuration. 

I've made some changes there and now I can connect with pgAdmin III

However the VB connection still doesn't work and any advice on that would be appreciated.

---

### Post by doas777 on 2011-03-09
I do .net rather than vb6, but one thing I notice missing from your connection string is an initialCatalog (the database you will be logging on to).

this site may be a good resource for you:
[http://www.connectionstrings.com/](http://www.connectionstrings.com/)

---

### Post by JohnInNacogdoches on 2011-03-09
> **doas777 said:**
> I do .net rather than vb6, but one thing I notice missing from your connection string is an initialCatalog (the database you will be logging on to).

this site may be a good resource for you:
[http://www.connectionstrings.com/](http://www.connectionstrings.com/)


I finally got logged in. no initalCatalog parameter, but there was a location parameter

---

