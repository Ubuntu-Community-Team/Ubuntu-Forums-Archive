---
title: "HOWTO: Install Ekiga with voipcheap account"
date: 2006-11-29
forum: Tutorials
---

### Post by aliyanage on 2006-11-29
Hi all,
After having a few issues I got my ekiga working using SIP with a voipcheap.com account. Thought some of you might be interested in how I did it:

**1. [www.voipcheap.com](www.voipcheap.com)**
Go to voipcheap.com register and make yourself an account.

**2. Start Ekiga**
Go to Applications/Internet/Ekiga Softphone (installed by default in Ubuntu)

**3. Cancel configuration druid**
Cancel the configuration druid and go to Edit/Accounts and click Add.

**4. Adding SIP account**
**Account name:** *VoipCheap (free to choose)*
**Protocol:** *SIP*
**Registrar:** *sip.voipcheap.com*
**Username:** *(username from voipcheap)*
**Password:** *(password from voipcheap)*
**Authentication Login:** *(username from voipcheap)*
**Realm/Domain:** *voipcheap.com*
**Registration Timeout:** *3600*

And then close accounts window.

**5. Preference settings**
-Go to *Edit/Preferences*
-Go to *General/SoundEvents* and set alternative output device to *default*.
-Go to *Protocols/NetworkSettings*
 **NAT Traversal Method:** *STUN*
 **Stun Server:** *stun.voipcheap.com*
 and then click on **Apply**.
-Go to *Protocols/SIPSettings*
 **Outbound Proxy:** *sip.voipcheap.com*
-Go to *Devices/AudioDevices*
 **Audio Devices Output Device:** *default*
 **Audio Devices Input Device:** *default*

And that's it, worked fine with me and I am doing my free landline calls to most of the countries :-D

---

### Post by hikaricore on 2006-11-29
Unless I'm missing something you have to download their client software to create an account now.  >.<  Hopefully wine can handle it, otherwise I'll be booting win2k in vmware lol.

---

### Post by canard on 2006-11-29
hi,

Very interesting... 
I've been using wengo for a long time and the rates are the same, except that you get 300 minutes free calls per 7 days during 90 days. Am I right?
And then you have to top up your account to get back the free calls for the next 90 days.

My question is how much is the minimum  you can put on your account and is the quality very good? You don't have "free" calls with wengo but i find it just like a regular phone, so i won't switch unless it is really as good....

thx

---

### Post by aliyanage on 2006-11-29
@hicaricore
sorry yes you'll have to download the client and then create urself an account. Such a long time ago I did it that I've already forgot about it ](*,)

---

### Post by aliyanage on 2006-11-29
@canard
ur right, you get 300 free minutes per week during 90 days. After that I had to top up my account with about 6 euros, but the cool thing is that it's not really like a contribution to voipcheap, those 6 euros will go to your account and you'll be able to use them as well. I use them usually for mobile calls.

I never used wengo, all I knew about was skype which doesn't include any free calls and is about twice as expensive as voipcheap.com.

I would just give it a try... :-D

---

### Post by canard on 2006-11-29
thx for your answer.

I just figured out that you can try it for free with calls limited to 1 minute or so. I guess i should go for it and see if i am happy with the quality. My credit is almost 0 on wengo so i can switch to it if sounds ok.

---

### Post by hikaricore on 2006-11-29
> **aliyanage said:**
> @hicaricore
sorry yes you'll have to download the client and then create urself an account. Such a long time ago I did it that I've already forgot about it ](*,)

Ok for those of you looking to do this entirely from within linux, you'll need to install the client: [Download Link]("http://www.voipcheap.com/getfrommirror.php?file=voipcheapCOM&lang=en").

Then you'll need to (asuming from your home dir and the file is on your desktop) run:

```
wine Desktop/setupvoipcheapCOM.exe
```

after it installs which it will do slowly....

You'll need two dll files in your *~/.wine/drive_c/windows/system32* directory:

[pdh.dll]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/P/pdh.dll/5.1.2600.2180/download.html")  and  [odbcbcp.dll]("http://www.dlldump.com/download-dll-files.php/dllfiles/O/odbcbcp.dll/download.html")

Cnce you've placed them there, you're safe to run:

```
wine "C:\\Program Files\\VoipCheapCom\\VoipCheapCom.exe"
```

Create your account, get all the info you need together... then delete the horrid piece of windows trash (optional).  Proceed with aliyanage's plans for voip domination.

The end.

---

### Post by hikaricore on 2006-11-29
...or maybe watch the registration process fail horribly... looks like I may be running vmware after all :/

(results may vary)

---

### Post by creaturex on 2006-11-29
something wrong with a dns option, specifically the DNS_QUERY_BYPASS_CACHE is not implemented.

---

### Post by aliyanage on 2006-11-30
> **hikaricore said:**
> Ok for those of you looking to do this entirely from within linux, you'll need to install the client: [Download Link]("http://www.voipcheap.com/getfrommirror.php?file=voipcheapCOM&lang=en").

Then you'll need to (asuming from your home dir and the file is on your desktop) run:

```
wine Desktop/setupvoipcheapCOM.exe
```

after it installs which it will do slowly....

You'll need two dll files in your *~/.wine/drive_c/windows/system32* directory:

[pdh.dll]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/P/pdh.dll/5.1.2600.2180/download.html")  and  [odbcbcp.dll]("http://www.dlldump.com/download-dll-files.php/dllfiles/O/odbcbcp.dll/download.html")

Cnce you've placed them there, you're safe to run:

```
wine "C:\\Program Files\\VoipCheapCom\\VoipCheapCom.exe"
```

Create your account, get all the info you need together... then delete the horrid piece of windows trash (optional).  Proceed with aliyanage's plans for voip domination.

The end.

Thanks for the add Hikaricore 8)

---

### Post by bodhi.zazen on 2006-11-30
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by hikaricore on 2006-11-30
> **creaturex said:**
> something wrong with a dns option, specifically the DNS_QUERY_BYPASS_CACHE is not implemented.

Yea it's trying to manually reread the dns server and bypass the windows dns cache rofl... i don't think that's going to work :)


Eh I tried.  Ran this in vmware with win2k and managed to setup an account.

---

### Post by edemark on 2007-02-05
hi you might get some better results if you use x-lite 3.0 for w in do ze installed in wine (not a normal one but in the wine created by ie4linux script) [http://appdb.winehq.org/appview.php?iVersionId=2419](http://appdb.winehq.org/appview.php?iVersionId=2419)
the prog works with many voip provider ie freecall (it might work with voipcheap too)
so far i was only able to ring but not to talk though but this might be because of my settings or some dll issues.

good luck

if you manage to talk then give some feedback here

pd i just observed that my reply is really off topic as this thread is on how to use voipcheap qith ekiga sorry

---

### Post by tiepolo on 2007-03-07
i cannot understand why i cannot register in ekiga with cheapVoip or Internetcalls or anything else but ekiga account.

I followed the instruction, and many other similar in the net, but no results; the same procedure allows me to use tweakle with no problems, so it is not a router's firewall problem (no pc firewall)

I'm using edgy.

If someone can help me.............

Pb with tweakle is poor quality of sound for conterpart (this doesn't happen in XP with Cheapvoip software, so it is a tweakle problem)

---

### Post by tiepolo on 2007-03-08
i would add that ekiga works fine in 6.06 - it is definitely a problem with 6.10. Problems in quality of voice are the same as tweakle.

Any idea?

Paolo

---

### Post by PurplePenguin on 2007-03-23
Ekiga works fine in 6.10.  

And just as an update to this thread, the betamax voip sites (voipdiscount.com, voipbuster.com, etc) don't have a time limit anymore.  You need to put 10 euros into your account, but now they'll stay there until you use them up.  So if you only talk for your 120 "free" days, and only to free numbers, you'll have free voip for as long as the company will be around, it seems. :)

---

### Post by elias85 on 2007-09-02
Anyone to guide us using Ekiga with a 12voip account? (not using windows,wine)

---

### Post by aliyanage on 2007-09-03
hmm... haven't tried it yet but I think it will be similar to the voipcheap account. Did you already try or do you have the possibility to install this software on a windows machine?

If so you'll probably get all the details off, that you need for ekiga, after you've installed it.

regards
aliyanage

---

### Post by elias85 on 2007-09-04
ok i got connected on my voipdiscount account.how do i send messages to another voipdiscount user who is online.i tried it(he is using windoze).. he send me a msg but nothing came. PLEASE HELP me figure out whats going on. I open 5000-5100 ports as well on my modem/router

---

### Post by niceguy123 on 2007-09-04
voipdiscount  seems to be the same exact deal as voipcheap is it not the same company?

I went though the whole process of downloading and installing voipcheap on a xp machine and then setting up the account in Ekiga. 

After that I dialed a few numbers (including my own landline) I hear a ringing in Ekiga but no ring on the landline itself. So I'm not sure why its not working. 

Then I went into the viopcheap home page and tried buying some credit (because I thought that maybe its not giving me the free minutes because I had no real credit), but couldn't because they only have somekind of UK payment systems (no paypal etc.) 

Is this really worth the bother?


Aside for that can someone tell me 
1.how ekiga works with skype ?
2. Can Ekiga run mutipule accounts at the same time like Pidgin?
3. And what about buddy lists (where) do they show?
4. What about Ekiga.net itself does it have voip to phone and how much does it cost?

BTW - I sent a test SMS via voipcheap site (without any money in the account, so it was free). I work very nicely, Anyone know how many free SMS you can send via there site? Is it a daily quota? Is there a way to send sms via ekiga? And what about sending out lists? I saw something about a hack for sending out lists via icq.

Thanks,

---

### Post by sad_iq on 2007-09-20
> **elias85 said:**
> Anyone to guide us using Ekiga with a 12voip account? (not using windows,wine)
Try this link...it will let you register without any download: [http://www.12voip.com/en/websignup.php](http://www.12voip.com/en/websignup.php)
 I'm still trying to use ekiga with it thou...as I am unable to see what servers they're using :(

---

### Post by elias85 on 2007-10-07
has anyone succeded running 12voip either via wine, either using vmware(loading windoze etc) or via Ekiga?

---

### Post by sad_iq on 2007-10-09
Is anyone still interested in this thread??
 Anyway for those interested in the free* countries that the operators offer check out Lowrateip ([http://www.lowratevoip.com/en/index.html](http://www.lowratevoip.com/en/index.html)). It basically has the same countries like 12voip has but they only give 200 free minutes a week and only during 30 days. I'm still looking for the price to pay for the free days subscription :(
 The good thing is that they provide the sip settings...so ekiga should work with it. Also you can register on the web form to get a username and password without using the windows only version of the program. If anyone has used it please post if the connection works ok and the signal is aceptable!!!
 Haha...found another one: [http://www.justvoip.com/en/newsflash.html](http://www.justvoip.com/en/newsflash.html) same free countries, more free minutes...but no sip server yet :(

---

### Post by pashlit on 2007-11-01
Worked fine with Ubuntu 7.10. I had to unplug the router to get it working. Seems like its not able to detect my NAT. Will dig into it. If anybody knows how to tweak the router, please post here.
I am not able to send chat messages and see them in Ekiga. Does anybody know how to solve this if possible.
Tnx

---

### Post by pashlit on 2007-11-02
Got it working with router. Just install the firewall. The one I installed didnt have to be configured. I didnt dig into it. All I needed is just working VoipCheap with Egna. Works cool and sound quality is perfect.
Take care,

[http://www.fs-security.com/](http://www.fs-security.com/) - this is good firewall by the way.

---

### Post by dJnEvS on 2008-03-22
I got my 12voip account working with Ekiga..
using the same info as 'lowratevoip'

[http://www.lowratevoip.com/en/sipp.html](http://www.lowratevoip.com/en/sipp.html)

At General:
[quote=website]SIP port : 5060
	Registrar : sip.lowratevoip.com
	Proxy server : sip.lowratevoip.com
	Outbound proxy server : leave empty
	Account name : your lowratevoip username
	Password : your lowratevoip password
	Display name/number : your lowratevoip username or voipnumber
	Stunserver (option) : stun.lowratevoip.com[/quote]

Good luck

Sorry that i post in a outdated topic, just wanted to share it with everyone!

---

### Post by manolomanolo on 2008-06-27
> **hikaricore said:**
> Ok for those of you looking to do this entirely from within linux, you'll need to install the client: [Download Link]("http://www.voipcheap.com/getfrommirror.php?file=voipcheapCOM&lang=en").

Then you'll need to (asuming from your home dir and the file is on your desktop) run:

```
wine Desktop/setupvoipcheapCOM.exe
```

after it installs which it will do slowly....

You'll need two dll files in your *~/.wine/drive_c/windows/system32* directory:

[pdh.dll]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/P/pdh.dll/5.1.2600.2180/download.html")  and  [odbcbcp.dll]("http://www.dlldump.com/download-dll-files.php/dllfiles/O/odbcbcp.dll/download.html")

Cnce you've placed them there, you're safe to run:

```
wine "C:\\Program Files\\VoipCheapCom\\VoipCheapCom.exe"
```

Create your account, get all the info you need together... then delete the horrid piece of windows trash (optional).  Proceed with aliyanage's plans for voip domination.

The end.


It crashes on my Ubuntu 8.04 just after installing VoipCheap through wine.
[IMG]http://img211.imageshack.us/img211/875/screenshotul6.png[/IMG]

---

### Post by pashlit on 2008-06-27
> **manolomanolo said:**
> It crashes on my Ubuntu 8.04 just after installing VoipCheap through wine.
[IMG]http://img211.imageshack.us/img211/875/screenshotul6.png[/IMG]

Hey, VoipCheap soft does not work in Ubuntu. At least I haven't heard about it so far. The goal of this thread is how to make VoipCheap account work with Ekiga. Its pretty simple as u see.
Good luck.

---

### Post by n2dabloo on 2008-06-27
Please help, I finally got my video to work by following your directions.  I cannot get my audio to work at all.  Thanks in advance...
And that's it, worked fine with me and I am doing my free landline calls to most of the countries :-D[/QUOTE]

---

### Post by manolomanolo on 2008-06-30
> **pashlit said:**
> Hey, VoipCheap soft does not work in Ubuntu. At least I haven't heard about it so far. The goal of this thread is how to make VoipCheap account work with Ekiga. Its pretty simple as u see.
Good luck.

I was just [answering to hikaricore]("http://ubuntuforums.org/showpost.php?p=1823988&postcount=7")
It doesn't work with Ekiga anyway. Maybe I have some sound problems since Ekiga crashes when both testing audio through the configuration druid and when making a phone call. In this last case it crashes but I do receive the phone call (I tried calling from my laptop to my own landlina and mobile phone) but of course I can hear nothing.

Any suggestion please?
Thanks.

---

### Post by emil_p8 on 2008-07-02
12voip WORKS with Ekiga: SIP server is connectionserver2.12voip.com

---

### Post by sbszulu on 2008-07-04
I got mine to work but I can hear the person on the other end but they cannot hear me. This seems to be a sound problem.

Any advise?

I'm using Hardy Heron.

---

### Post by energy10 on 2009-11-13
has anyone managed to install 12voip on ubuntu 9.10 ? I ' ve been trying but no luck :(

---

### Post by krige on 2010-04-12
> **aliyanage said:**
> 
**2. Start Ekiga**
Go to Applications/Internet/Ekiga Softphone (installed by default in Ubuntu)

**3. Cancel configuration druid**
Cancel the configuration druid and go to Edit/Accounts and click Add.

**4. Adding SIP account**
**Account name:** *VoipCheap (free to choose)*
**Protocol:** *SIP*
**Registrar:** *sip.voipcheap.com*
**Username:** *(username from voipcheap)*
**Password:** *(password from voipcheap)*
**Authentication Login:** *(username from voipcheap)*
**Realm/Domain:** *voipcheap.com*
**Registration Timeout:** *3600*

And then close accounts window.

**5. Preference settings**
-Go to *Edit/Preferences*
-Go to *General/SoundEvents* and set alternative output device to *default*.
-Go to *Protocols/NetworkSettings*
 **NAT Traversal Method:** *STUN*
 **Stun Server:** *stun.voipcheap.com*
 and then click on **Apply**.
-Go to *Protocols/SIPSettings*
 **Outbound Proxy:** *sip.voipcheap.com*

Great howto, thanks! Ekiga configuration panels have changed a little bit lately though. I have tried to follow those instructions as much as I could but didn't manage to connect because of the following error:

Could not register (Transport error)

I did the following:
- Edit / Accounts
- Accounts / Add a SIP account

Name: VoipCheap
Registar: sip.voipcheap.com
User: (username from voipcheap)
Authentication user: (username from voipcheap)
Password: (password from voipcheap)
Timeout: 3600 (default)

- Edit / Preferences
- Protocols / SIP Settings

Outbound proxy: sip.voipcheap.com
Forward URI: sip: (default)
Send DTMF as: INFO (tried also with RFC2833 but didn't work)

Is there anything missing here? What's the correct Forward URI value?

---

### Post by pashlit on 2010-04-12
> **krige said:**
> Great howto, thanks! Ekiga configuration panels have changed a little bit lately though. I have tried to follow those instructions as much as I could but didn't manage to connect because of the following error:

Could not register (Transport error)

I did the following:
- Edit / Accounts
- Accounts / Add a SIP account

Name: VoipCheap
Registar: sip.voipcheap.com
User: (username from voipcheap)
Authentication user: (username from voipcheap)
Password: (password from voipcheap)
Timeout: 3600 (default)

- Edit / Preferences
- Protocols / SIP Settings

Outbound proxy: sip.voipcheap.com
Forward URI: sip: (default)
Send DTMF as: INFO (tried also with RFC2833 but didn't work)

Is there anything missing here? What's the correct Forward URI value?
U basically dont need to enter any other parameters. Just login, password and sip.voipcheap.com for transport. Might change some settings for your audio devices. My guess u r on WIFI network. For some reason Ekiga has a bug with x64 systems. On my 386 desktop it works fine, on my AMDx64 laptop I receive the same error as yours. Wait till new Ubuntu comes out. It might fix those bugs. Or u can try to mess with firewall but I am too lazy to do that. Good luck.

---

### Post by krige on 2010-04-12
> **pashlit said:**
> Might change some settings for your audio devices. My guess u r on WIFI network. For some reason Ekiga has a bug with x64 systems. On my 386 desktop it works fine, on my AMDx64 laptop I receive the same error as yours. Wait till new Ubuntu comes out. It might fix those bugs. Or u can try to mess with firewall but I am too lazy to do that. Good luck.

Thanks. I am connected to a wired network, using Ubuntu 10.04 64 bit: it must be related with the bug with x64 systems you mentioned.

---

### Post by pashlit on 2010-04-12
> **krige said:**
> Thanks. I am connected to a wired network, using Ubuntu 10.04 64 bit: it must be related with the bug with x64 systems you mentioned.
Could be. I use sjphone on my AMDx64. I was gonna write a tutorial on that but its easy to figure out how it works and i am just too lazy. Just enter sip.voipcheap.com as  your server and u r good to go. [http://www.sjlabs.com/sjp.html](http://www.sjlabs.com/sjp.html).

It works fine and looks way better than Ekiga. Ekiga is simpler though. I ll wait till final release of 10.4 and look into it. I dunno why they havent fixed that bug yet.

---

### Post by krige on 2010-04-12
I have filed a bug report. In case anyone else wants to add their experience this is the URL:
[https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/561735](https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/561735)

---

### Post by jrfmason on 2010-06-03
> **pashlit said:**
> Could be. I use sjphone on my AMDx64. I was gonna write a tutorial on that but its easy to figure out how it works and i am just too lazy. Just enter sip.voipcheap.com as  your server and u r good to go. [http://www.sjlabs.com/sjp.html](http://www.sjlabs.com/sjp.html).

It works fine and looks way better than Ekiga. Ekiga is simpler though. I ll wait till final release of 10.4 and look into it. I dunno why they havent fixed that bug yet.

I have tried everything with Ekiga I think but I am new to this. Skype and Gizmo dial straight through my router and switch but Ekiga always has (transport error) I have opened ports but nothing. I am using wired. Your explanation for Ekiga made sense even if I cant get it to work so I thought I would give sjphone a go on Lucid. You say its easy to figure out but not for me, please write that tutorial. jrfm

---

### Post by krige on 2010-08-17
I tried Ekiga today and it worked! Now the status of the VoipCheap account appears as "registered".

I did the following:
- Edit / Accounts
- Accounts / Add a SIP account

Name: VoipCheap
Registar: sip.voipcheap.com
User: (username from voipcheap)
Authentication user: (username from voipcheap)
Password: (password from voipcheap)
Timeout: 3600

I left the default SIP settings, that is:

- Edit / Preferences
- Protocols / SIP Settings

Outbound proxy: 
Forward URI: sip:
Send DTMF as: INFO

There are still three things missing:

[LIST=1]
[*]I couldn't find a way to set my phone number as caller like in VoipCheap under Windows (that is my calls appear as anonymous calls);
[*]it does not show the amount of avaible credit nor the cost of the current call or sms;
[*]it does not import automatically your contacts from your VoipCheap account.
[/LIST]

Does anybody know whether any of the above things are possible in Ekiga?

---

### Post by littlepeon on 2010-09-06
afaik, those things aren't available for ekiga...

it is the same as the differences in skype windows and skype linux.

skype windows has many more features (cleaner interface, browser toolbar, will import numbers from webpages, more options in tinterface, etc) than the linux version...

however more people are developing in linux, so there is hope that software interfaces will become more uniform.

good luck
-Peon

---

### Post by marer13 on 2011-11-23
It doesn't seem to be working....

I've followed the steps as in here and in the Ekiga window it says:

**Could not register sip:***my user name***.**

Any ideas?

---

### Post by pashlit on 2011-11-23
> **marer13 said:**
> It doesn't seem to be working....

I've followed the steps as in here and in the Ekiga window it says:

**Could not register sip:***my user name***.**

Any ideas?

I cant believe I am still subscribed to this old thread. LOL I am not a Ubuntu user anymore since it went in wrong direction of developing the right distro. Anyway, I am always willing to help.
Nowadays you dont have to do anything to get it working. Just make sure you configured your router correctly if you are on wireless. The settings for port opening/forwarding are on Ekiga website.
Also firewall might block the signal. You can configure firewall or just turn it off.

sudo ufw disable

and if you need to turn it back on: sudo ufw enable

Cheers.

---

### Post by marer13 on 2011-11-24
I don't think it's the router, because I managed to set it up on another laptop a few weeks ago. I just don't remember how I did that.... It was something in the settings in Ekiga, maybe something in Preferences?

---

