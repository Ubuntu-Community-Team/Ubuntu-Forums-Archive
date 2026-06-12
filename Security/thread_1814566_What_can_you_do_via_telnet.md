---
title: "What can you do via telnet?"
date: 2011-07-29
forum: Security
---

### Post by hakermania on 2011-07-29
Ok, let's say you now that a server has some ports open and you connect to one of them via telnet.
Connection is not refused, you get connected normally.
For example, I connected to a web site to its port 80 but whatever I type the response (in the terminal(!) is
```
<html>
<head><title>400 Bad Request</title></head>
<body bgcolor="white">
<center><h1>400 Bad Request</h1></center>
<hr><center>nginx</center>
</body>
</html>
```
So, I wonder, what can somebody do through (the deprecated (because of ssh?)) telnet if it is connected to a port?:o

---

### Post by haqking on 2011-07-29
> **hakermania said:**
> Ok, let's say you now that a server has some ports open and you connect to one of them via telnet.
Connection is not refused, you get connected normally.
For example, I connected to a web site to its port 80 but whatever I type the response (in the terminal(!) is
```
<html>
<head><title>400 Bad Request</title></head>
<body bgcolor="white">
<center><h1>400 Bad Request</h1></center>
<hr><center>nginx</center>
</body>
</html>
```So, I wonder, what can somebody do through (the deprecated (because of ssh?)) telnet if it is connected to a port?:o

it depends on the port its connected to.

if you telnet to port 25 then you can send emails  via smtp commands etc

---

### Post by CharlesA on 2011-07-29
I use telnet to check to see if a port is open..

---

### Post by haqking on 2011-07-29
> **CharlesA said:**
> I use telnet to check to see if a port is open..


indeed, it often goes overlooked as a troubleshooting or connectivity tool

---

### Post by CharlesA on 2011-07-29
> **haqking said:**
> indeed, it often goes overlooked as a troubleshooting or connectivity tool
Indeed. I'd say it's "bad" for a remote connectivity tool (ssh is way better), but it has other uses. ;)

---

### Post by haqking on 2011-07-29
> **CharlesA said:**
> Indeed. I'd say it's "bad" for a remote connectivity tool (ssh is way better), but it has other uses. ;)
  
of course ssh all the way for remote admin

---

### Post by enimeizoo on 2011-07-29
You can do whatever the server program listening to the port allows you to do, assuming you know it's language.
If you connect to a website (httpd) on the port 80, you can send
```
GET
```to get the homepage. 
If you connect to a sshd, you will have to negotiate SSL connection before authentication...

It is just a minimal client. It just sends the text you type to another program.

At least it is my understanding of it.

---

### Post by scorp123 on 2011-07-29
> **hakermania said:**
>  So, I wonder, what can somebody do through telnet ... Read mails, send mails, surf the web, ... :D

---

### Post by Sef on 2011-07-31
> Quote:
Originally Posted by haqking  
indeed, it often goes overlooked as a troubleshooting or connectivity tool

Indeed. I'd say it's "bad" for a remote connectivity tool (ssh is way better), but it has other uses. 

The reason telnet is not recommended for remote connections is that it sends things in the clear, i.e., unencrypted. Anyone monitoring the transmissions can read what is being transmitted.

---

### Post by haqking on 2011-07-31
> **Sef said:**
> The reason telnet is not recommended for remote connections is that it sends things in the clear, i.e., unencrypted. Anyone monitoring the transmissions can read what is being transmitted.


I know that ;-)

i would never use telnet for remote admin.

---

