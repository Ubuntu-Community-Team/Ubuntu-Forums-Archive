---
title: "[SOLVED] Since there's nowhere else to post this..."
date: 2007-10-08
forum: Windows
---

### Post by Happy_Man on 2007-10-08
There are no good Windows forums out there... so I'm going to post this here. If a mod wants to remove it, OK. I have no idea what's up with this anyway.

So here's the problem:

When I resized my Windows partition after much defragging of the HDD, I saw that it had become ridiculously slow. Like, processor never dipped below 50%, and the system pretty much became unusable. 

So I booted into safe mode, and uninstalled all the crap that was on there, disabled Norton Internet Security from starting up with msconfig, and while I was at it, disabled some other random things that I had no idea were running, and rebooted into normal Windows. 

Wonder of wonders! My system was FAST AGAIN!!! I was amazed, and in the middle of patting myself on the back, when I opened up IE to test Internet. 

It gave me an error. "Internet Explorer could not display the webpage." I checked the network. All OK. Power-cycled the router. OK. My laptop could get internet, so it was the computer's problem. The connectivity wizard they give you with IE7 says that it can't get a response with either http, ftp, or whatever. 

But the odd thing is, Windows Update is pulling down its updates just fine. The router is blinking, the internet is humming, but neither IE nor Firefox nor Opera will display any webpages. Ping and ipconfig both report no errors. I am... baffled, to say the least. 

So, I can only think that I need to forward some ports. Never had to do that before, so that may or may not be it. Any other suggestions would be welcome!

P.S.: I'm only doing this as a pet project, to see whether my Windows install was salvageable. And, while we're here, why does Word hang at the splash screen, and only start in safe mode? I'm so *confused*....

---

### Post by shad0w_walker on 2007-10-08
Have you checked your DNS settings?

---

### Post by cogadh on 2007-10-08
What were those other "random things" that you disabled? Is it possible that one of them was related to networking?

---

### Post by Happy_Man on 2007-10-08
Well, I'm not sure it matters very much, as I enabled most of it afterwards.... the only things I didn't enable were the Norton services and some string that is called this by msconfig: ```
##Id_String1.6844F930_1628_4223_B5CC_5BB94B879762##
```

Is that the networking service? 

@shad0w_walker:

How do I check those? 

And here's some other information:

I cleaned up the computer using NTREGOPT and CCleaner. Was that bad? It had internet while it was running slow as hell, but after it sped up (eg, after I rebooted after doing all these changes and stuff), it lost internet.

---

### Post by shad0w_walker on 2007-10-08
They will be in your network settings, you should be able to find them in the same tab as manual IP config. If you want to check they are working, try pinging a website you know the IP address of as well as the domain name.

Google server IP/Domain:

Domain

```
py-in-f99.google.com
```

IP

```
64.233.167.99
```

If you can ping the server by IP but not by name then your problem is the DNS servers.

---

### Post by Happy_Man on 2007-10-08
Both of those work.... but pinging myself doesn't. Is that supposed to happen?

And where is manual IP config? As I said, I am a complete n00b in Windows.

---

### Post by shad0w_walker on 2007-10-08
If memory serves (Been a while and my VMs are unavailable right now)

Right click on network places (Assuming its on your desktop)
Select properties and it should open up a window showing your network connections.
Right click on the network connection (Assuming you only have one)
Goto properties, should give you a window with the details of the network card that connection is using. In the middle of the window there will be a list box showing a list of protocols.
Select Internet Protocol (TCP/IP) (Its normally at the bottom of the list) and click the properties button below the list box.
This will open up a dialog that lets you select manual or automatic and lets you configure your IPs manually.

Only problem with all this is that if both those pings work then your DNS servers are fine, which means my idea about whats up is wrong.

---

### Post by Happy_Man on 2007-10-08
Hmmm.. perhaps I uninstalled the Verizon software by mistake. Thanks for your help.

---

### Post by cogadh on 2007-10-08
> **Happy_Man said:**
> Well, I'm not sure it matters very much, as I enabled most of it afterwards.... the only things I didn't enable were the Norton services and some string that is called this by msconfig: ```
##Id_String1.6844F930_1628_4223_B5CC_5BB94B879762##
```

Is that the networking service? 
That is a network zero configuration service called Bonjour that is installed with certain products from Adobe (specifically Adobe Creative Suite) and other providers. It is actually an open source Apple product and it may be part of your Verizon software. It might be required for networking to work correctly, but if you want to remove Bonjour correctly:

1. Open a Windows command prompt and type the following command:
"C:\Program Files\Bonjour\mDNSResponder.exe -remove"
2. Navigate to the following folder in Windows Explorer: C:\Program Files\Bonjour
3. Rename the mdnsNSP.dll file in that folder to mdnsNSP.old
4. Restart your computer
5. Delete the the Program Files\Bonjour folder

---

### Post by Happy_Man on 2007-10-08
Hmmm... OK. I thought that it was a virus or something. Perhaps enabling it will do the trick. I'll go check.

UPDATE: **sigh** That didn't do it either. One other thing I just noticed is that Google Talk loads its connection just fine, but neither IE nor Firefox will display. Is this a permission problem? Is something blocking internet access selectively? I know I had Norton Antivirus and all that BS on here, but I got rid of it. Could that have crippled my internet?

---

### Post by angryfirelord on 2007-10-08
Interesting, Windows is hard for Linux users. :)

Uh, anyway, if you have a firewall enabled (including the Windows firewall), disable it & see if your web browser can view pages.

---

### Post by Happy_Man on 2007-10-08
No, I have no firewall. Any other ideas?

---

### Post by digital_exhaust on 2007-10-08
I don't know how to fix your problems... but there are good Windows forums out there... some just have a bad reputation... are big and have a lot of rude people that like to flame a lot.... but others seem to strike the perfect balance, and if you look [H]ard enough you just might be able to find the answers to your questions.... 

I hope that my advice is helpful.....

Quick edit... remove Norton completely... rather it helps or not, your machine will run much better...and there is no reason you should have to forward any ports simply to display web pages..

---

### Post by Happy_Man on 2007-10-09
Well, you guys might be interested in how I eventually fixed this, so here goes: 

I went back into msconfig services tab, and enabled all of them, since that was about when the problem started. Well, since Norton was about the only thing I disabled, I had a suspicion that it was the problem. Well, it was. Once I had disabled the firewall Norton gave, the internet came back. 

To everybody who suggested I disable the firewall:

Sorry I snubbed you all, and you were right. The reason I said that is because I thought I had uninstalled Norton before I did all this (and the Add/Remove Software dialog still doesn't show it) but they were there anyway, insidiously blocking internet access all along. In that respect, Norton is kind of like a virus in and of itself. Well, I disabled all Norton service except the Internet Connection one (just in case) and so far, everything is just dandy. 

@digital_exhaust:

Yeah, I guess I should remove Norton completely. But, as I stated above, Windows thinks it's gone. Is there any other way to go in and just purge the system of it? If not, it's all right, my system kinda pretends it doesn't exist now anyway. 

Again, everyone, thanks for all the help.

---

### Post by JBAlaska on 2007-10-09
There are utility's on the norton website for completly removing it, You need to know what exact version you are using as the remove utility's are version specific.

Here's a link:
```
http://service1.symantec.com/SUPPORT/nip.nsf/docid/2001090510510636
```

---

### Post by Shazaam on 2007-10-09
nm I'm too slow lol.

---

### Post by qpieus on 2007-10-09
> **Happy_Man said:**
>  Norton is kind of like a virus in and of itself.

Boy you got that right. When I ran windows I stayed as far away as possible from anything Norton. I remember installing norton utilities, I think it was called, and my computer about ground to a standstill. It was crazy.

---

