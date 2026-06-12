---
title: "firewall in ubuntu"
date: 2012-03-05
forum: Security
---

### Post by colorfultrixe on 2012-03-05
Hi can any one tell this old lady how to activate the fire wall in simple terms please in ubuntu.
I have just purchased Ubuntu from your site and installed in on my lappy
got to say im impressed with all the gagets I love it. I should mention im wireless with a router and WPA 2PSK But I feel I need some anti virus and firewall as I do all my private stuff on lappy
Also can you tell me when you put a gaget in the launcher and it becomes full can you have another launcher and how do you do this.
I thank you for such a great forum and hope some one can help with my issues :confused:

---

### Post by sffvba[e0rt on 2012-03-05
In a terminal (pressing Ctrl+Alt+t should work to open one) enter the following:

```
sudo ufw enable
```

Enter your password (there will be nothing to show you are typing but it is working) and hit enter.


404

---

### Post by colorfultrixe on 2012-03-05
How do I open a terminal dear I also forgot to say I install fire starter today and it would'nt enable so I put it in recycle bin
I have re edited cause I've now enable the fire wall is their anything else I need to do regauding this hun
Thank you I have many more Q to ask but not today this girl is sleepy

---

### Post by Diametric on 2012-03-05
There shouldn't be much more you need to do other than exercise caution regarding what sites you go to and how you store/manage you personal information.  Remember, it all starts with physical security.    

Good luck and have fun!

---

### Post by CharlesA on 2012-03-05
Just a note: Firestarter conflicts with ufw, so it would be unwise to use both. I would suggest removing firestarter and just using ufw.

---

### Post by haqking on 2012-03-05
> **colorfultrixe said:**
> How do I open a terminal dear I also forgot to say I install fire starter today and it would'nt enable so I put it in recycle bin
I have re edited cause I've now enable the fire wall is their anything else I need to do regauding this hun
Thank you I have many more Q to ask but not today this girl is sleepy

ctrl+alt+t will open a terminal.

If you are in 11.04 and above using unity then in the dash type terminal.

Also you need to remove firestarter as it is an old project but more importantly it conflicts with ufw/gufw.


read these for more information

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

[How to setup a firewall in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1876124")

---

### Post by Ms. Daisy on 2012-03-05
> **colorfultrixe said:**
> 
I have just purchased Ubuntu from your site and installed in on my lappy

What do you mean you "purchased" it?

---

### Post by HermanAB on 2012-03-06
Howdy,

Relax dude...

Linux pretty much IS a firewall.  If you did a default install, then you don't need to do anything special.  You don't need to run UFW or Firestarter, or any one of a zoo of firewall scripts. 

Why? because by default, Ubuntu doesn't run any naughty services.

So, just relax and enjoy your Ubuntu system.

---

### Post by Ms. Daisy on 2012-03-06
> **HermanAB said:**
> Howdy,

Relax dude...

Linux pretty much IS a firewall.  If you did a default install, then you don't need to do anything special.  You don't need to run UFW or Firestarter, or any one of a zoo of firewall scripts. 

Why? because by default, Ubuntu doesn't run any naughty services.

So, just relax and enjoy your Ubuntu system.
I'd like to read more about that. Where did you get this information? Please give us some links because I can't seem to find any supporting evidence for your statements.

---

### Post by haqking on 2012-03-06
> **HermanAB said:**
> Howdy,

Relax dude...

Linux pretty much IS a firewall.  If you did a default install, then you don't need to do anything special.  You don't need to run UFW or Firestarter, or any one of a zoo of firewall scripts. 

Why? because by default, Ubuntu doesn't run any naughty services.

So, just relax and enjoy your Ubuntu system.

respectfully, that only pertains to the incoming side of a firewall and the "open" ports argument often used.

Outbound rules are just as important, regardless of listening services naughty or not, application code can be exploited to bind to arbitrary ports and hackers/crackers can create reverse connections.

Tight outbound policies can help to eliminate this.

Security is a process not a product.
Security is a process not a state.

Cheers

---

### Post by colorfultrixe on 2012-03-06
Thank you all for your replies
MS daisy I know I could have downloaded a ISO file but I decided to buy helps towards making Ubuntu better and saves me a lot of hassle loll.
I have had problems trying to download avast today tried to install and got error 
so I tried again  and I got all this script a full page of it on my screen so I quickly came out of the browser, I need to scan my PC as I use an external drive and usb sticks in windows and I don't want to infect the other PC.

---

### Post by Diametric on 2012-03-06
I'm not entirely sure from your post - but I want to be clear that you do not need an anti-virus for you Ubuntu computer.  Some may argue with this, but it is my opinion that if you observe safe Internet browsing practices and employ common sense, there is no need for one.  Just my opinion.

---

### Post by haqking on 2012-03-06
> **Diametric said:**
> I'm not entirely sure from your post - but I want to be clear that you do not need an anti-virus for you Ubuntu computer.  Some may argue with this, but it is my opinion that if you observe safe Internet browsing practices and employ common sense, there is no need for one.  Just my opinion.

I would say it was pretty clear from what was said

> I need to scan my PC as I use an external drive and usb sticks in windows and I don't want to infect the other PC

---

### Post by Diametric on 2012-03-06
How does your reply remain on topic or contribute to the OP's issue in any way?  The post wasn't clear to me - it still isn't, regardless of you reposting a portion of it.  Let's try and keep this constructive.

My reply, if not originally clear, was made to inform the new Ubuntu user that Anti virus is not needed on an Ubuntu install - in my opinion.  She may need it for her MS machine(s) but not with a Linux OS.

---

### Post by haqking on 2012-03-06
> **Diametric said:**
> How does your reply remain on topic or contribute to the OP's issue in any way?  The post wasn't clear to me - it still isn't, regardless of you reposting a portion of it.  Let's try and keep this constructive.

My reply, if not originally clear, was made to inform the new Ubuntu user that Anti virus is not needed on an Ubuntu install - in my opinion.  She may need it for her MS machine(s) but not with a Linux OS.

I never meant to cause you distress, your OP mentioned it was not clear to you so i pointed it out.

it is on topic because it never left and shows the part where the OP shows that they want to scan files for use on windows hence the need for AV which is the reason why people use AV in Linux for the most part.

The OP asked about use of AV on her Ubuntu install due to file sharing with windows.

To the OP, the firewall questions have been addressed above and as for AV, then most people tend to use clamAV for scanning for infected files for sharing with windows and it is in the software centre or post your Avast issues here for further help.


Cheers

---

### Post by Ms. Daisy on 2012-03-06
Diametric, perhaps your lack of clarity comes from this: AVs nearly all scan for Windows viruses, so running an AV on Linux to detect Linux viruses isn't very useful or effective. Often it results in false positives.

**However**

Protecting files on Linux that are shared with Windows seems to be a pretty common reason for running an AV on Ubuntu.  See [here]("https://help.ubuntu.com/community/Antivirus") for some other reasons, (also quoted below):

[LIST]
[*]to scan a Windows drive in your PC
[*]to scan a Windows-based network attached server or hard drive
[*]to scan Windows machines over a network
[*]to scan files you are going to send to other people
[*]to scan e-mail you are going to forward to other people
[*]some Windows viruses can run with Wine.
[/LIST]

---

### Post by CharlesA on 2012-03-06
haqking and Ms. Daisy covered tbe AV angles pretty thoroughly. I use BitDefender instead of clamVM (too many false positives) or avast (never used it) when I am scanning files that are being shared with windows.

---

