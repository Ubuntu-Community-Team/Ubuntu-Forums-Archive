---
title: "Pen Test IIS"
date: 2011-01-27
forum: Security
---

### Post by CNM on 2011-01-27
Hi ,

I need to do a pentest on a Microsoft IIS webserver to test the efficiency of the HIPS i have installed on ...
any suggestions concerning tools or methods to simulate attacks so that i can check if the HIPS will detect them ?
also , any suggestions of good HIPS out there ?

Thanks

---

### Post by BbUiDgZ on 2011-01-27
start here - [http://www.backtrack-linux.org/](http://www.backtrack-linux.org/) 
I also find this site a good resource
[http://www.darknet.org.uk/](http://www.darknet.org.uk/) 

you may also wanna look [at this link to a microsoft product](http://www.microsoft.com/downloads/en/details.aspx?familyid=02be8aee-a3b6-4d94-b1c9-4b1989e0900c&displaylang=en)

---

### Post by CNM on 2011-01-27
> **BbUiDgZ said:**
> start here - [http://www.backtrack-linux.org/](http://www.backtrack-linux.org/) 
I also find this site a good resource
[http://www.darknet.org.uk/](http://www.darknet.org.uk/) 

you may also wanna look [at this link to a microsoft product]("http://www.microsoft.com/downloads/en/details.aspx?familyid=02be8aee-a3b6-4d94-b1c9-4b1989e0900c&displaylang=en")


Hi ,
thanks for your reply :)

i already use backtrack for 2 years now
and also am familiar with MBSA

the thing is i need an attack that probably all HIPS would detect ... just to make sure that the one i have installed is running well ...
also i need a good HIPS for an IIS server (other than snort cause i need one installable on windows)

any suggestions ? :)

---

### Post by bodhi.zazen on 2011-01-27
Snort will run on Windows.

This kind of activity is gray hat stuff at best and is not really supported on these forums.

First you are asking about a windows server -> we would ask you to ask for windows support on a windows forums.

Second you are not asking for support on getting any particular application running, you are asking for cracking tools. Honestly I am not sure what is included in Backtrack, but I would be surprised if it did not have tools.

If nothing else , port scan your server, a port scan is easy to perform and should, IMO, be detected.

Otherwise Google search your question ;)

---

### Post by CNM on 2011-01-27
> **bodhi.zazen said:**
> Snort will run on Windows.

This kind of activity is gray hat stuff at best and is not really supported on these forums.

First you are asking about a windows server -> we would ask you to ask for windows support on a windows forums.

Second you are not asking for support on getting any particular application running, you are asking for cracking tools. Honestly I am not sure what is included in Backtrack, but I would be surprised if it did not have tools.

If nothing else , port scan your server, a port scan is easy to perform and should, IMO, be detected.

Otherwise Google search your question ;)

actually this is why im asking ... i port scanned the server using ubuntu .
i got results and hardened some configs and the results im getting now are ok .
but my made me curious is that the HIPS did not pick up the port scan ! not even as probe !
this is why i was asking what kind of simulation all HIPS detect ...

---

