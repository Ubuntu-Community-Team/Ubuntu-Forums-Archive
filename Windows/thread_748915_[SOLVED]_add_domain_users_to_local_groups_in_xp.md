---
title: "[SOLVED] add domain users to local groups in xp"
date: 2008-04-07
forum: Windows
---

### Post by motoperpetuo on 2008-04-07
i'm studying for my MCSA on windows 2003, and i've got a little domain set up at home, consisting of just my server (a powerhouse six-year-old sony vaio with 256mb RAM) and one windows xp pro client. i've created several user objects in active directory on the server, but i'm not able to add them to local groups on the xp client.

on the real-life domain at work, i'm able to add users from active directory to local groups on a client computer by doing this (i'll use a user whose account name is "dilbert" as an example):

1) My Computer|Properties|Manage.
2) expand the Local Users and Groups node and click on Groups.
3) double-click on the group to which i want to add dilbert.
4) click Add
5) type the first few letters of "dilbert" and click OK.
6) choose dilbert from the list of user accounts that appears.

when i try this at home, the client computer doesn't seem to look in active directory on the server for user accounts, just on the local machine. i imagine it's just a setting or GPO i need to alter, but i can't figure it out (yes, i have joined the client computer to my domain).

thanks in advance for any help. i'm slogging through this windows certification stuff in hopes of someday getting a sys admin job and thus being more influential than the lowly desktop support guy i am now. i figure that way i can better do my part to spread linux and open-source software. and make more money.

---

### Post by rickyjones on 2008-04-08
Welcome to the Microsoft certs :P. I've been there and done that, so let me see if I can help.

When you click "Add" and it opens the window "Select Users, Computers, or Groups" you have three text areas. The first is Object Type. The second is Location. The third is where you type in the name of the object to add.

In the Location field, what does it say? It should say your domain name. If not then it is not searching the domain. Click the "Locations..." button to the right. Find your domain and select it.

I hope this points you in the correct direction.

Sincerely,
Richard

---

### Post by motoperpetuo on 2008-04-09
> **rickyjones said:**
> Welcome to the Microsoft certs :P. I've been there and done that, so let me see if I can help.

When you click "Add" and it opens the window "Select Users, Computers, or Groups" you have three text areas. The first is Object Type. The second is Location. The third is where you type in the name of the object to add.

In the Location field, what does it say? It should say your domain name. If not then it is not searching the domain. Click the "Locations..." button to the right. Find your domain and select it.

I hope this points you in the correct direction.

Sincerely,
Richard

actually, that's the problem: when i click the locations button, my domain isn't available, just the local machine. you would think that means my client isn't communicating with the domain controller, but i'm able to log on to the client, even with a user account that hasn't logged on before and hence doesn't have a cached profile.

any idea what might cause that? i asked one of the sys admins where i work and he was stumped too. also, thanks for taking time to try to help, i really appreciate it.

---

### Post by cprofitt on 2008-04-10
OK -- let me clarify...

Your client machine at home is joined to your domain and you are able to login?

This client machine at home is not joined to your work domain and is a difference machine?

Have you setup DNS/DHCP for your domain at home?

---

### Post by motoperpetuo on 2008-04-10
> **PrivateVoid said:**
> OK -- let me clarify...

Your client machine at home is joined to your domain and you are able to login?

This client machine at home is not joined to your work domain and is a difference machine?

Have you setup DNS/DHCP for your domain at home?

i was just using the domain at work as an example of a domain that has been set up properly by someone who knows what he's doing (unlike me). the domain i have set up at home is the one that's giving me problems.

i have DHCP set up at home, but from my router, not from my server (the server itself has a static IP address). i think DNS is working, because i'm able to ping all my windows clients by computer name (if i remember correclty...i'll verify that next time i fire up my windows machines). nevertheless, DHCP/DNS is probably a good direction in which to look. 

like i said, this is just a test domain on a typical home network, so it's probably something i missed when setting things up.

---

### Post by rickyjones on 2008-04-10
DHCP from the router is fine, just manually assign a DNS entry on the client computer and have it point to your domain controller. Trust me, it works this way.

The fact that when you click "Locations" and it does not even show the domain worries me. Can you browse to the domain through this window? Can you access shares on the server by using UNC paths?

Sincerely,
Richard

---

### Post by motoperpetuo on 2008-04-10
> **rickyjones said:**
> The fact that when you click "Locations" and it does not even show the domain worries me. Can you browse to the domain through this window? Can you access shares on the server by using UNC paths?

Sincerely,
Richard

that IS strange, isn't it? especially since i'm clearly able to log on to the domain. also, come to think of it, i'm pretty sure DNS is ok because i'm able to remote into the server from my client with the server's computer name. i'm going to do a little troubleshooting soon, hopefully tonight. hopefully i can figure this out, but as we know, actually knowing how to do stuff on a server is second-place to being able to memorize facts and questions from the book on these certification exams (unfortunately). it would be nice to get this working, but i think i'll be able to pass the test either way.

again, thanks for the help, both of you.

---

### Post by motoperpetuo on 2008-04-10
> **rickyjones said:**
> DHCP from the router is fine, just manually assign a DNS entry on the client computer and have it point to your domain controller. Trust me, it works this way.

that was it. it took me a little while to realize what you meant. that is, that i had to go into my TCP/IP properties and change from "obtain DNS server address automatically" and switch the radio button to "use the following DNS server addresses" and then add the ip address of my domain controller. i'm not exactly a genius with this stuff, yet.

one clue i got on another forum was that if you ping your server and get something like this (supposing your server is called "server01" and your domain is called "domain01"):

Pinging server01 [10.69.99.55] with 32 bytes of data:

you have a DNS problem. the domain should also be listed, like this:

Pinging server01.domain01.com [10.69.99.55] with 32 bytes of data:

anyway, looks like the problem is solved. i really, really appreciate the help.

---

### Post by rickyjones on 2008-04-11
> **motoperpetuo said:**
> that was it. it took me a little while to realize what you meant. that is, that i had to go into my TCP/IP properties and change from "obtain DNS server address automatically" and switch the radio button to "use the following DNS server addresses" and then add the ip address of my domain controller. i'm not exactly a genius with this stuff, yet.

one clue i got on another forum was that if you ping your server and get something like this (supposing your server is called "server01" and your domain is called "domain01"):

Pinging server01 [10.69.99.55] with 32 bytes of data:

you have a DNS problem. the domain should also be listed, like this:

Pinging server01.domain01.com [10.69.99.55] with 32 bytes of data:

anyway, looks like the problem is solved. i really, really appreciate the help.

I'm glad that you have it working! Congratz!

Sincerely,
Richard

---

