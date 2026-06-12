---
title: "Installing desktop on a Dell server"
date: 2011-05-04
forum: Server Platforms
---

### Post by Hopping_Ubu on 2011-05-04
I have been given the task of standing up a Intrusion Detection System for a network. I have been given a Dell 2950 server in which to do it, but I will not be the one who is responsible for maintaining once it is operational. I can function in the CLI environment, but I am not sure that others will be able to. My question is, can Ubuntu 10.10 desktop be installed on a Dell server? When I tried to do it, it hung up on the Ubuntu screen after the dots went through a couple of cycles blinking.

Any assistance would be greatly appreciated.

---

### Post by collisionystm on 2011-05-04
> **Hopping_Ubu said:**
> I have been given the task of standing up a Intrusion Detection System for a network. I have been given a Dell 2950 server in which to do it, but I will not be the one who is responsible for maintaining once it is operational. I can function in the CLI environment, but I am not sure that others will be able to. My question is, can Ubuntu 10.10 desktop be installed on a Dell server? When I tried to do it, it hung up on the Ubuntu screen after the dots went through a couple of cycles blinking.

Any assistance would be greatly appreciated.


use 10.04.

I have installed it on a 2950. Make sure to use 64 bit

---

### Post by arrrghhh on 2011-05-04
What are the users going to be managing?  There's a lot of webUI tools that make it very easy to run a headless server without users having to touch the CLI - obviously depending on what the users need.

Why the Desktop install hangs, I would assume video related.  What are the server's specs?  I don't know of anything off the top of my head that would outright prevent a Dell server from having Ubuntu Desktop on it, other than maybe video requirements...

---

### Post by wojox on 2011-05-04
Probably the graphics. You could get to the install screen and press F6 and choose "nomodeset". Better yet install Webmin for server maintenance if whoever takes it over isn't comfortable with the cli.

---

### Post by Hopping_Ubu on 2011-05-04
All, thank you for the inputs. 

collisionystm - Why 64 bit? What advantage does it have over the 32 version? :confused:

arrrghh - The user will be managing Snort. That is the only thing it will be running. 

wojox - I may try doing the F6 when I get to the install screen. I have been trying to find more information on Webadmin and how to properly install it. If that works, that would be the better route I believe, but I want to be prepared in the event that the system manager doesn't want to log in via a webui.


):P
Thank you all again.
Robert

---

### Post by arrrghhh on 2011-05-04
> **Hopping_Ubu said:**
> All, thank you for the inputs. 

collisionystm - Why 64 bit? What advantage does it have over the 32 version? :confused:

arrrghh - The user will be managing Snort. That is the only thing it will be running. 

wojox - I may try doing the F6 when I get to the install screen. I have been trying to find more information on Webadmin and how to properly install it. If that works, that would be the better route I believe, but I want to be prepared in the event that the system manager doesn't want to log in via a webui.


):P
Thank you all again.
Robert

It's called "[Webmin](http://webmin.com/)" and I'd just use the deb from their site - I don't think Ubuntu includes it in the repo's any longer because of how it updates the system (IIRC).

I didn't really use that feature in Webmin anyhow...

For SNORT - I've never used it myself, but I'm sure there's some sort of GUI options for it out there - just need to find something that will work for your environment, and webUI's are always a good choice since they are very OS agnostic ;).

---

### Post by Hopping_Ubu on 2011-05-04
> **arrrghhh said:**
> It's called "[Webmin]("http://webmin.com/")" and I'd just use the deb from their site - I don't think Ubuntu includes it in the repo's any longer because of how it updates the system (IIRC).

I didn't really use that feature in Webmin anyhow...

For SNORT - I've never used it myself, but I'm sure there's some sort of GUI options for it out there - just need to find something that will work for your environment, and webUI's are always a good choice since they are very OS agnostic ;).

Thanks again for your input. SNORT has a graphical interface once it is installed, but the last time I installed and ran it, I would need to restart it everyone once in awhile and definitely after power outages. I will have to find a script or something to get it to start when the server starts up.

---

