---
title: "Field-test to determine the behavior of your NAT-Router (please participate)"
date: 2007-11-20
forum: The Cafe
---

### Post by Andreas_Mueller_UNI-TUE on 2007-11-20
Hello,

we at the University of Tuebingen are investigating the behavior of Network Address Translation (NAT) with regard to NAT traversal. Today, most households use a Network Address Translator (NAT) integrated into their DSL-Router to connect to the internet. The NAT translates between the public and the private realm and creates a mapping for each outgoing connection. This works well as long as connections are established from the inside because the NAT is aware of all incoming packets and can forward them to the appropriate private host. But as soon as a user wants to provide a service behind a NAT, the NAT is not able to map inbound packets to this host because no state exists for these packets. This problem is called the NAT-Traversal Problem. There are already a number of approaches to solve this problem, but these approaches depend on the NAT behavior.

The implementation of a NAT is not standardized. The behavior of NATs not only varies from vendor to vendor, but also from type to type. To evaluate and test as many NATs as possible, we created a small application that determines the properties of a NAT and makes some connectivity tests with our test server.

Therefore, we kindly ask you to download the NAT-Tester and run it on your home computer. The test takes 1-2 minutes and is done automatically. After the test, you will be directed to an internet-page where you can provide some information about the tested NAT (vendor and model). The test client is available for Windows and Linux. The Source-Code can be found within the Linux package. If you have any questions, please contact us.

Visit **[http://gex.cs.uni-tuebingen.de](http://gex.cs.uni-tuebingen.de)** at your convenience to participate and to look at all the results.

Kind Regards
  Andreas Mueller and Andreas Klenk

---

### Post by ice60 on 2007-11-20
> **Andreas_Mueller_UNI-TUE said:**
> Hello,

we at the University of Tuebingen are investigating the behavior of Network Address Translation (NAT) with regard to NAT traversal. Today, most households use a Network Address Translator (NAT) integrated into their DSL-Router to connect to the internet. The NAT translates between the public and the private realm and creates a mapping for each outgoing connection. This works well as long as connections are established from the inside because the NAT is aware of all incoming packets and can forward them to the appropriate private host. But as soon as a user wants to provide a service behind a NAT, the NAT is not able to map inbound packets to this host because no state exists for these packets. This problem is called the NAT-Traversal Problem. There are already a number of approaches to solve this problem, but these approaches depend on the NAT behavior.

The implementation of a NAT is not standardized. The behavior of NATs not only varies from vendor to vendor, but also from type to type. To evaluate and test as many NATs as possible, we created a small application that determines the properties of a NAT and makes some connectivity tests with our test server.

Therefore, we kindly ask you to download the NAT-Tester and run it on your home computer. The test takes 1-2 minutes and is done automatically. After the test, you will be directed to an internet-page where you can provide some information about the tested NAT (vendor and model). The test client is available for Windows and Linux. The Source-Code can be found within the Linux package. If you have any questions, please contact us.

Visit **[http://gex.cs.uni-tuebingen.de](http://gex.cs.uni-tuebingen.de)** at your convenience to participate and to look at all the results.

Kind Regards
  Andreas Mueller and Andreas Klenk
steve gibson was going on about how one of his friends had just tested 60 routers for something, i can't remember what now. you could try asking at the mailing list.
[http://www.grcmail.com/mail.htm](http://www.grcmail.com/mail.htm)

---

### Post by Andreas_Mueller_UNI-TUE on 2007-11-20
Thanks for the hint.

We've already tested >80 Routers (see [www.gex.cs.uni-tuebingen.de](www.gex.cs.uni-tuebingen.de)) but most of them were located in Germany. So it would be just great to get some more results from other countries.

Thank you very much!

Andreas Mueller

---

### Post by juxtaposed on 2007-11-20
I did it, but I'm not sure of the firmware of my router so I left it blank.

---

### Post by popch on 2007-11-20
I tried to 'make' as instructed on your web page, using Ubuntu Linux 7.10. 

Make enters and leaves a few directories but otherwise appears to be doing nothing at all. Also, I can not find any file named NATTester.

Being an inordinately inept Linux user, I would require a bit more guidance in order to perform the test.

---

### Post by Andreas_Mueller_UNI-TUE on 2007-11-20
Sorry I just found a little mistake on the English version of our webpage:
After "make" you have to switch to the src directory in order to execute NATTester:

./configure
make
cd src
./NatTester

Sorry for the inconvenience,

Andreas Mueller

---

### Post by juxtaposed on 2007-11-20
> After "make" you have to switch to the src directory in order to execute NATTester:

It said how to do it the right way in the readme file though :)

---

### Post by popch on 2007-11-20
> **Andreas_Mueller_UNI-TUE said:**
> Sorry I just found a little mistake on the English version of our webpage ...

Now it works. Test done. I am not quite sure but it appears that I have some ports forwarded on my device. Does this affect your test in any way?

---

### Post by Flying caveman on 2007-11-20
I did the test.

Just curious, what is the purpose of this? 

Good: Improve security
Evil: Block P2P / VoIP/ home web servers

here's the wiki [http://en.wikipedia.org/wiki/NAT_traversal](http://en.wikipedia.org/wiki/NAT_traversal) but its beyond my comprehension.

---

### Post by jrusso2 on 2007-11-20
You guys are a very trusting bunch.  I am not so sure I would trust something that someone put up on their first post on  a forum to run on my box.

---

### Post by Flying caveman on 2007-11-20
> **jrusso2 said:**
> You guys are a very trusting bunch.  I am not so sure I would trust something that someone put up on their first post on  a forum to run on my box.

You don't trust Germans or zomething like zat?

---

### Post by Daveski on 2007-11-20
> **jrusso2 said:**
> You guys are a very trusting bunch.  I am not so sure I would trust something that someone put up on their first post on  a forum to run on my box.

Especially as the OP stated that it would perform some connectivity tests with their server - apparently both outgoing and incoming.

---

### Post by NineseveN on 2007-11-20
> **jrusso2 said:**
> You guys are a very trusting bunch.  I am not so sure I would trust something that someone put up on their first post on  a forum to run on my box.

The force is strong with this one.

---

### Post by jflaker on 2007-11-20
> **jrusso2 said:**
> You guys are a very trusting bunch.  I am not so sure I would trust something that someone put up on their first post on  a forum to run on my box.

WOW.......Does anyone really know what they did?  It is interesting that a few have jumped at a possible social engineering plot to ALLOW unknown connections through their routers and system!!!!  Unbelievable!  This is how to destabilize your security and allow Hackers into your network!!!

---

### Post by jrusso2 on 2007-11-20
I am not saying this is or isn't the case here but if I  couldn't read the code to see what it does I would be hesitant.

---

### Post by jdong on 2007-11-20
In this case it seems like the test suite is legitimate -- seems like a hole-punching test to see if your router allows this behavior (many IM/P2P apps already employ holepunching)


But the points raised are ABSOLUTELY correct -- it's concerning how easily people were willing to compile and execute some random source code posted on the net.

---

### Post by jflaker on 2007-11-20
> **jdong said:**
> In this case it seems like the test suite is legitimate -- seems like a hole-punching test to see if your router allows this behavior (many IM/P2P apps already employ holepunching)


But the points raised are ABSOLUTELY correct -- it's concerning how easily people were willing to compile and execute some random source code posted on the net.

When stuff like this is posted, it is absolutely OK to be as nervous as a long tail cat in a room full of rocking chairs........I just prefer to remove myself from that room until the rocking chairs are chocked so they don't rock!

---

### Post by jdong on 2007-11-20
I should add, especially during a time where we've had several incidents of dangerous commands posted and warnings not to do things without thinking, I'm especially disheartened by the judgement of our community.

Well I'm going to assume everyone who reported on the test has read through the source code of the testing app, understood what it is doing, compiled in a restricted environment, and ran under a limited user account with an AppArmor/SELinux profile controlling its access to the system. Right?. Right?

---

### Post by jflaker on 2007-11-20
> **jdong said:**
> I should add, especially during a time where we've had several incidents of dangerous commands posted and warnings not to do things without thinking, I'm especially disheartened by the judgement of our community.

Well I'm going to assume everyone who reported on the test has read through the source code of the testing app, understood what it is doing, compiled in a restricted environment, and ran under a limited user account with an AppArmor/SELinux profile controlling its access to the system. Right?. Right?

yeah....sure.....Ya see...I don't even know what you are talking about....I need to read more!  lol

---

### Post by popch on 2007-11-21
> **jrusso2 said:**
> You guys are a very trusting bunch.  I am not so sure I would trust something that someone put up on their first post on  a forum to run on my box.

I did it on my testing box which will get scrubbed in a short while.

---

### Post by popch on 2007-11-21
> **jrusso2 said:**
> I am not saying this is or isn't the case here but if I  couldn't read the code to see what it does I would be hesitant.

You can read the code. Whether you did or not is another story. Also, whether reading it is of any use to you.

Also, there's the matter of the URL where the code originated from. It is not the first time I got code from that particular Uni. I even believe that their site is one of the more responsive mirrors for quite a few goodies. However, I would have to ga back to my notes to be sure about that. Don't take my word on this.

---

### Post by Andreas_Mueller_UNI-TUE on 2007-11-21
> **Flying caveman said:**
> I did the test.

Just curious, what is the purpose of this? 

Good: Improve security
Evil: Block P2P / VoIP/ home web servers

here's the wiki [http://en.wikipedia.org/wiki/NAT_traversal](http://en.wikipedia.org/wiki/NAT_traversal) but its beyond my comprehension.

The purpose of this test is to gain knowledge about the actual behavior of NATs regarding different NAT-Traversal techniques such as Hole-Punching, UPnP, Relaying... Especially for Transport Protocols other than UDP (TCP and SCTP) NAT-Traversal is still an unsolved problem. 

As NATs differ from model to model (please see our results-page) it is necessary for a NAT-Traversal solution to consider several Traversal-techniques and apply them according to the situation and the NAT. 

One of our research goals at the University of Tuebingen is to develop a new NAT-Traversal framework helping legacy applications to work accross NATs properly. The NAT-Tester is just one part of it and will help us to understand the behavior of current NATs.

---

### Post by jrusso2 on 2007-11-21
> **popch said:**
> You can read the code. Whether you did or not is another story. Also, whether reading it is of any use to you.

Also, there's the matter of the URL where the code originated from. It is not the first time I got code from that particular Uni. I even believe that their site is one of the more responsive mirrors for quite a few goodies. However, I would have to ga back to my notes to be sure about that. Don't take my word on this.

I didn't download it I am not that trusting.  I am speaking for the people who did.
In this case it appears to be ok.  But it could have not been.

---

### Post by jdong on 2007-11-21
> **Andreas_Mueller_UNI-TUE said:**
> 
One of our research goals at the University of Tuebingen is to develop a new NAT-Traversal framework helping legacy applications to work accross NATs properly. The NAT-Tester is just one part of it and will help us to understand the behavior of current NATs.

After reviewing the sourcecode and looking into your work, I have no doubt that this project is legitimate and not dangerous to our users. Please understand that none of my comments above were specifically directed at your project -- keep up your good work.

The point I was trying to make is had this been someone else with a more malicious intent, he could've easily set up a trojan source archive that does extremely destructive things when compiled or run. So please be careful and review things before running them on your computer. Linux is not magically immune to every exploit -- if you let your guard down there's not much the OS can do to help.

---

### Post by Andreas_Mueller_UNI-TUE on 2007-11-21
> **jdong said:**
> After reviewing the sourcecode and looking into your work, I have no doubt that this project is legitimate and not dangerous to our users. Please understand that none of my comments above were specifically directed at your project -- keep up your good work.

You're are absolutely right, you should always be paranoid about running unknown software on your machine. 

We also know that this is the main reason for not getting as many results as we initially thought, but we're trying to be as transparent as possible. 
Unfortunately in this case there's no other way that running a piece of software behind the NAT.

Anyway, maybe now other users might want to participate, too.
Thanks.

---

### Post by rabid9797 on 2007-11-21
done and uploaded :)

---

### Post by Rinzwind on 2007-11-21
done :)

Always happy to help. Though I always wait for someone to post a review of the code ;) :D

---

### Post by scrooge_74 on 2007-11-21
i got this errors when I try to make 

Making all in src
make[1]: se ingresa al directorio `/tmp/linuxTester-0.1/src'
Making all in tools
make[2]: se ingresa al directorio `/tmp/linuxTester-0.1/src/tools'
source='xmlRead.cxx' object='xmlRead.o' libtool=no \
        DEPDIR=.deps depmode=none /bin/sh ../../depcomp \
        g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"linuxTester\" -DVERSION=\"0.1\" -I.    -I/usr/include/libxml2    -c -o xmlRead.o xmlRead.cxx
../../depcomp: line 566: exec: g++: not found
make[2]: *** [xmlRead.o] Error 127
make[2]: se sale del directorio `/tmp/linuxTester-0.1/src/tools'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/tmp/linuxTester-0.1/src'
make: *** [all-recursive] Error 1

I am using Debian Lenny

---

### Post by p_quarles on 2007-11-21
> **scrooge_74 said:**
> -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"linuxTester\" -DVERSION=\"0.1\" -I.    -I/usr/include/libxml2    -c -o xmlRead.o xmlRead.cxx
../../depcomp: line 566: exec: g++: not found
Looks like that's where the problem is. Have you got the build tools installed?
```
# apt-get install build-essential
```

---

### Post by scrooge_74 on 2007-11-21
as a matter of fact no, I havent use this laptop for compiling anything since installing Debian,  but when it had Ubuntu I had all necesary packages installed.

Problem solve thanks

---

### Post by boast on 2007-11-21
hmmm, how long does it take? It doesn't go past

```
$ ./NatTester eth0

Your NAT-Box has the following properties:

Could not reach the stun server - check server name is correct
Preserves port number
Does not support hairpin of media


No UPnP-Device found.


no UPnP device found



```

---

### Post by jflaker on 2007-11-21
> **popch said:**
> I did it on my testing box which will get scrubbed in a short while.

Hmmm......good idea to set up a VirtualBox install of Ubuntu so this stuff can be done with limited damage if such malicious code is not caught before compiling and running stuff.  A VIrtualBox host can be killed faster than a regular hardware system if things go wrong.

Now i need another Hard drive!

---

### Post by popch on 2007-11-22
> **jflaker said:**
> Hmmm......good idea to set up a VirtualBox install of Ubuntu so this stuff can be done with limited damage if such malicious code is not caught before compiling and running stuff.

Good thinking. I decided not to use a virtual machine in this case because the purpose of the test was to determine the behaviour of the network, and I am not sure whether a virtual network influences the result in some way.

With VMWare, you can attach your VM with NAT to the LAN, too.

---

### Post by Andreas_Mueller_UNI-TUE on 2007-11-22
> **popch said:**
> Good thinking. I decided not to use a virtual machine in this case because the purpose of the test was to determine the behaviour of the network, and I am not sure whether a virtual network influences the result in some way.

That's actually true, if Vmware is configured to connect to the LAN via a NAT then the result not only depends on the router but also on the vmware-NAT.

> **boast said:**
> hmmm, how long does it take? It doesn't go past
```
$ ./NatTester eth0
Your NAT-Box has the following properties:
Could not reach the stun server - check server name is correct
Preserves port number
Does not support hairpin of media
no UPnP-Device found.

```

There seems to be a problem reaching the STUN-Server. Either it was temporarily down or some outgoing packets were blocked by your firewall. 
The test should only take 1-2 minutes.
Is eth0 the device connected to the router? Maybe you are using WLAN?

---

