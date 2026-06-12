---
title: "Apache and windows XP"
date: 2008-11-21
forum: Windows
---

### Post by Uchiha_madara on 2008-11-21
Hi every one...


I'm sorry to say about WinXp in Ubuntu forums but >>

I installed Xampp in My PC and Apache Works very fine..

but when i installed the Anti virus Apache is stopped 

what is the reason????

and how can i fix it??

---

### Post by drubin on 2008-11-21
> **Uchiha_madara said:**
> Hi every one...
I'm sorry to say about WinXp in Ubuntu forums but >>
I installed Xampp in My PC and Apache Works very fine..
but when i installed the Anti virus Apache is stopped 
what is the reason????
and how can i fix it??

Hi

Is apache running? Open up the task manager and see if it is running.
What happens when you hit localhost in a browser?
if you open up a cmd run netstat -l to check if apache is listening on the correct port?

Ps I have already suggested this thread be moved to the windows section as this has little to do with programming or Ubuntu server platforms

---

### Post by Uchiha_madara on 2008-11-21
> s apache running? Open up the task manager and see if it is running.

no ...
Apache doesn't work ...
it gave me a message after the installation that 
"the port 80 is bussy " Apache is failed ..

-- i need to ask :
 maybe the Anti virus make the Port 80 is Busy and Disabled Apache 
is that true or not??


> What happens when you hit localhost in a browser?
there is no result

> if you open up a cmd run netstat -l to check if apache is listening on the correct port?

look.. this is the result..and thank you very much

> C:\Documents and Settings\ahmed>netstat -a

Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    ahmed-dc604cb58:epmap  ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:microsoft-ds  ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:3306   ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:5051   ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:5101   ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:1145   cs119.msg.ac4.yahoo.com:5050  ESTABLISHED
  TCP    ahmed-dc604cb58:1153   sip45.voice.re2.yahoo.com:https  ESTABLISHED
  TCP    ahmed-dc604cb58:1932   38.118.85.21:http      ESTABLISHED
  TCP    ahmed-dc604cb58:1028   ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:1144   localhost:30606        ESTABLISHED
  TCP    ahmed-dc604cb58:1152   localhost:30606        ESTABLISHED
  TCP    ahmed-dc604cb58:1242   localhost:1243         ESTABLISHED
  TCP    ahmed-dc604cb58:1243   localhost:1242         ESTABLISHED
  TCP    ahmed-dc604cb58:1246   localhost:1247         ESTABLISHED
  TCP    ahmed-dc604cb58:1247   localhost:1246         ESTABLISHED
  TCP    ahmed-dc604cb58:1931   localhost:30606        ESTABLISHED
  TCP    ahmed-dc604cb58:30606  ahmed-dc604cb58:0      LISTENING
  TCP    ahmed-dc604cb58:30606  localhost:1144         ESTABLISHED
  TCP    ahmed-dc604cb58:30606  localhost:1152         ESTABLISHED
  TCP    ahmed-dc604cb58:30606  localhost:1931         ESTABLISHED
  TCP    ahmed-dc604cb58:30606  localhost:1939         TIME_WAIT
  TCP    ahmed-dc604cb58:netbios-ssn  ahmed-dc604cb58:0      LISTENING
  UDP    ahmed-dc604cb58:microsoft-ds  *:*
  UDP    ahmed-dc604cb58:isakmp  *:*
  UDP    ahmed-dc604cb58:1049   *:*
  UDP    ahmed-dc604cb58:1080   *:*
  UDP    ahmed-dc604cb58:1320   *:*
  UDP    ahmed-dc604cb58:4500   *:*
  UDP    ahmed-dc604cb58:5051   *:*
  UDP    ahmed-dc604cb58:ntp    *:*
  UDP    ahmed-dc604cb58:1900   *:*
  UDP    ahmed-dc604cb58:ntp    *:*
  UDP    ahmed-dc604cb58:1054   *:*
  UDP    ahmed-dc604cb58:1182   *:*
  UDP    ahmed-dc604cb58:1183   *:*
  UDP    ahmed-dc604cb58:1186   *:*
  UDP    ahmed-dc604cb58:1187   *:*
  UDP    ahmed-dc604cb58:1900   *:*
  UDP    ahmed-dc604cb58:ntp    *:*
  UDP    ahmed-dc604cb58:netbios-ns  *:*
  UDP    ahmed-dc604cb58:netbios-dgm  *:*
  UDP    ahmed-dc604cb58:1900   *:*

---

### Post by slavik on 2008-11-21
Moving this threads to the Windows forum.

---

### Post by drubin on 2008-11-21
> **Uchiha_madara said:**
> no ...
Apache doesn't work ...
it gave me a message after the installation that 
"the port 80 is bussy " Apache is failed ..

-- i need to ask :
 maybe the Anti virus make the Port 80 is Busy and Disabled Apache 
is that true or not??

there is no result

look.. this is the result..and thank you very much
1) We know it is not working..(Elde you would not be asking the question)  I asked if it was running. (Sorry if english is not your native language but note the difference)

2) This was my thinking.

2) Not 100% sure about the netstat yet but will look into it.

---

### Post by drubin on 2008-11-21
> **slavik said:**
> Moving this threads to the Windows forum.

Thanks I am sure the people in here will be better suited to this task.

@OP what anti virus did you install? I have had no issues with Xampp on windows under both AVG and Avast.

---

### Post by cmat on 2008-11-21
There may be an application already running on your PC that's blocking the port for apache. Also personal firewalls will create some issues with apache. I got apache working on Windows XP when I was still using it.

---

### Post by drubin on 2008-11-21
> **cmat said:**
> There may be an application already running on your PC that's blocking the port for apache. Also personal firewalls will create some issues with apache. I got apache working on Windows XP when I was still using it.

ODD question Have you installed SKYPE? 
[http://www.tcd.ie/iss/internet/skype.php](http://www.tcd.ie/iss/internet/skype.php)

---

### Post by Uchiha_madara on 2009-01-25
> **drubin said:**
> Thanks I am sure the people in here will be better suited to this task.

@OP what anti virus did you install? I have had no issues with Xampp on windows under both AVG and Avast.

i am using ESET nod32 ......
this anti virus uses the same port of Apache ....

i found the solution ...Choose one of Both :
1 - to install Xampp before Any Antivirus..
2 - or open the Port's Log and change the Port of Apache to Any Port you like...

whatever ....Ubuntu & linux in General the best environment for Apache and PHP works 

thank you all

---

### Post by Izek on 2009-01-26
> **Uchiha_madara said:**
> whatever ....Ubuntu & linux in General the best environment for Apache and PHP works

You've obviously have never had the time to install EasyPHP then.

---

### Post by Uchiha_madara on 2009-02-03
> **Izek said:**
> You've obviously have never had the time to install EasyPHP then.

Explain Please !

Because I don't know anything about programming php5 under Linux

---

### Post by Izek on 2009-02-03
> **Uchiha_madara said:**
> Because I don't know anything about programming php5 under Linux

easyPHP doesn't run php5 by default, sorry. Then again, I don't usually code in php5.

Go get easyPHP from easyphp.org and install it on your windows machine if you want.

You can upgrade easyPHP's PHP version by [clicking here](http://www.easyphp.org/faq.php#35).

EasyPHP shouldn't conflict with AVG, as I've used it.

---

