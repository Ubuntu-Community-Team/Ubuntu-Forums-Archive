---
title: "Push Server"
date: 2012-11-07
forum: Server Platforms
---

### Post by pgp_protector on 2012-11-07
I'm probably Overthinking my problem but I'm trying to learn anyways.

Intro:  I'm running 2 servers (Development & Live) 
Live Server is Running Ubuntu Linux 11
Development Server is Running Ubuntu Linux 12
Both are running on converted Windows Boxes, but are servicing less than 100 clients.

The server running MySQL for the Database, Apache for Web Services (Primarily used via SOAP & WSDL to custom C# .NET Applications)

Right now any changes in the database have to be polled for, with our user count it's not a real issue (each active user might send a SOAP Request every 500ms for a Check of Timestamps of the tables)

Now what I want to do is Configure this as a PUSH Server.  So when there are any changes, the Ubuntu server will PUSH out a notification to all active users that the Data has been updated.  I'm hoping to have this work both on the local network and to any offsite clients.

We're also looking at adding an Android Application to subscribe to the PUSH Server for notifications of data changes.

Question:
1) Can Apache be configured as a PUSH Server (If so, how?)
2) If not, do I need something like Meteor (and can I install that in parallel with Apache?)

---

### Post by SeijiSensei on 2012-11-08
Sounds more like a task that the application should be handling itself when it processes an INSERT.

---

### Post by pgp_protector on 2012-11-08
> **SeijiSensei said:**
> Sounds more like a task that the application should be handling itself when it processes an INSERT.

But how would the client application.
1) know who also is connected ?
2) send an update request to all other connected clients ?

---

### Post by koenn on 2012-11-09
It's always going to depend on your clients - a server can only "push" something to a client that is listening for or otherwise awaiting input. 

So how you implement this server-side depends on what you have client-side. 

I'm guessing more often than not this sort of functionality would be an implementation of Remote Procedure Call, but according to wikipedia it can also be achieved by a http server, i.e. by streaming or with "long polling"
[http://en.wikipedia.org/wiki/Push_technology#HTTP_server_push](http://en.wikipedia.org/wiki/Push_technology#HTTP_server_push)


so, yes, you can do this with Apache. 
How ? -> depends on the clients. At that point, your question becoms more of a coding question than a server question, imo.

---

### Post by pgp_protector on 2012-11-09
After some testing & coding.
1) Meteor will run fine with Apache, I just modified the port it's listing to for subscriptions / commands.
2) Open only the subscription port in the firewall and direct it to the Ubuntu Box.
3) on the SOAP Server.php script, add new function to send notices as required.
4) Coded the .NET Dll to subscribe to the server for updates.

so far it's working.
If I run any "change in database" command I get the push notification, and the apps that are subscribed to it get it.

Now to create an android app so subscribe to the "BugReport" Channel :D

---

