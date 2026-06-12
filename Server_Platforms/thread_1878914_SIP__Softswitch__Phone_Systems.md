---
title: "SIP / Softswitch / Phone Systems"
date: 2011-11-10
forum: Server Platforms
---

### Post by bsntech on 2011-11-10
Hello all,

Got something that I'm looking at doing - but not sure if it is even feasible.

Overall synopsis - I'd like to get a group of phone numbers from the phone company.  These numbers would then be setup to be forwarded to some kind of VoIP system so I would then be able to control how the calls are answered, forwarded, etc.

Can't say that I understand much about this process.  I just know that there are SIP Gateway Services - that can be purchased from providers such as Verizon.  They then allow you to route multiple phone numbers to a PBX or system.

I found a program called FreeSwitch that appears to work on Linux/Ubuntu.

Is the process just as simple as ordering the SIP Gateway Services from a phone provider, requesting a block of phone numbers, and then having a program like FreeSwitch installed on an Ubuntu server - that then somehow connects with the phone provider for call routing?

---

### Post by jonobr on 2011-11-10
Hey there


Firstly Id recommend you take a look at something like [PBX in a flash]("http://nerdvittles.dreamhosters.com/pbxinaflash/downloads/")


This is a full featured PBX based on the asterisk softswitch.
(There are others out there similar in nature eg incredible pbx, ferepbx etc)
There are two routes you can then go, you can buy a analog board (FXO ports) which will have a bunch of numbers associated with them and map them to extensions. There would be the Idea of direct dial in (DID) where people can be called directly,
or a pilot number and then extensions that people have to call.

On the other hand you could have your calls handled by a voip providor , there are tonnes out there.

What i really recommend you do though, is seach for a document called PIAF without tears, it gives a great overview of setups and goes on to configuring the whole thing

---

