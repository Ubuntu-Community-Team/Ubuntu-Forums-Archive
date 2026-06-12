---
title: "Windows application through Ubuntu Server"
date: 2011-09-30
forum: Server Platforms
---

### Post by jstugs on 2011-09-30
A co-worker and I inherited an internal network setup for our testing equipment. We learned enough to get the system up and running, and it has been functioning for months without issue, but we are running into an issue. The network is mostly used because we are not allowed to connect the testing equipment to the corporate network. The testing equipment uses the server as a file server, storing the test programs until the operator places them on the machine and runs the test.

Here is my question. I now have a windows program that needs to talk to a piece of equipment through the server(using it as a router). We have tried opening ports with no luck. Is this the right approach or is there something we need to do differently. The IPtables are setup(not by us) and functioning for their intended purpose.

Thanks a lot.

---

### Post by An Sanct on 2011-09-30
Welcome to the forums!

About the question: It is slightly irelevant what OS want to do what, server OS is important, everithing else is a different tier.

So, if I understand this here correctly, we are talking about three-tier system here 

A->B->C

Where Client A (OS unimportant) communicates to Server B (Ubuntu) to Client C (other machine).

Well :) that is all I could conclude and from here on it would be just wild guessing, so please, do provide more data.

I'm interested in:
Ubuntu version, Communication protocol, is there a Windows alternative, is the server headless? Please provide as much data as you possibly can, as I see it is a business type question, I urge you not to provide too much info ;) its all on a "need to know" basis.

---

### Post by jstugs on 2011-09-30
You have the setup correct, however client C is testing equipment with no OS. The end goal is using the equipments configuration software to control the tester.

It is Ubuntu Server 11.04 and is not headless. 

Im not sure of the windows alternative question. Are you asking if i can use a windows server instead of Ubuntu? If that is the question, the answer is no, because there are security protocols involved and the windows alternatives are the corporate network and therefore not allowed. 

Please excuse me. I am self taught and this project was handed to us to figure out(we are ubuntu desktop users and they figured why not). I may not know all the terminology so please bare with my ignorance.

Also, I must note that I do not have access to server right now. I am looking for things to research and learn about until i am able to sit in front of the computer again.

---

### Post by An Sanct on 2011-09-30
> **jstugs said:**
> You have the setup correct, however client C is testing equipment with no OS. The end goal is using the equipments configuration software to control the tester.

So it is Client *A* (any OS) -> Server *B*, controlling some peripheral *C*

> **jstugs said:**
> It is Ubuntu Server 11.04 and is not headless.
Great :) additional applications with a GUI can be added with no further effort (effort like RDC, putty, ssh, telnet, etc...)

> **jstugs said:**
> Im not sure of the windows alternative question. Are you asking if i can use a windows server instead of Ubuntu? If that is the question, the answer is no, because there are security protocols involved and the windows alternatives are the corporate network and therefore not allowed.

Actually what I wanted to hear was, if it has been done with some windows software yet. If the answer is still no, please tell me how the *B* is communicating with *A* and *C*. So generally with *A* it should be TCP/IP, UTP or something like that and with *C* it should be USB/COM/LPT/maybe even disk writing - HDD (somehow HDD was the logical thing to me)
  
> **jstugs said:**
> Please excuse me. I am self taught and this project was handed to us to figure out(we are ubuntu desktop users and they figured why not). I may not know all the terminology so please bare with my ignorance.
I know of noone who has a diploma about Linux here :) I am a self taught developer also :) just keen for new adventures, thats all ;)

> **jstugs said:**
> Also, I must note that I do not have access to server right now. I am looking for things to research and learn about until i am able to sit in front of the computer again.

Okay :) word of advice, before I fall asleep (its late here) always backup any system file, you make changes to ... having backups is not as much of an overhead as reinstalling.

PS. okay ... really late here ... please tell me about the way you wish the computers and peripheral to communicate (first few sections) and I'll do my best to help you.

Cheers! And have a nice week end!

---

### Post by jstugs on 2011-09-30
> 
Actually what I wanted to hear was, if it has been done with some windows software yet. If the answer is still no, please tell me how the *B* is communicating with *A* and *C*. So generally with *A* it should be TCP/IP, UTP or something like that and with *C* it should be USB/COM/LPT/maybe even disk writing - HDD (somehow HDD was the logical thing to me)
  
I have connected it to the windows servers just to see if it worked and it do. I know the software will communicate with the device just not through the ubuntu server.


> 
Okay :) word of advice, before I fall asleep (its late here) always backup any system file, you make changes to ... having backups is not as much of an overhead as reinstalling.

yes everything gets backed up...learned that the hard way a long time ago.

> 
PS. okay ... really late here ... please tell me about the way you wish the computers and peripheral to communicate (first few sections) and I'll do my best to help you.

The way it works it that the testing station sits in an area on the floor. I use the software that come with the device to communicate with the peripheral via the LAN. I can send data to it and it also retrieves the test results from it. So its a two way system all controlled by a gui on my windows machine.

Thanks for the help!!

---

