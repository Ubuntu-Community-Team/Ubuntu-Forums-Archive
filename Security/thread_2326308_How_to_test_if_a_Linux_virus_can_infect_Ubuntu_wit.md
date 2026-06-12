---
title: "How to test if a Linux virus can infect Ubuntu without any antivirus?"
date: 2016-05-30
forum: Security
---

### Post by j2ee on 2016-05-30
I google and saw people talking about EICAR. Base on my understanding EICAR is a DOS execute file so it cannot simulate a Linux virus, it just simulate a Windows virus. So anyway to test if a Linux virus can infect Ubuntu without any antivirus?

---

### Post by deadflowr on 2016-05-30
*Thread moved to **Security**.*

---

### Post by ajgreeny on 2016-05-30
As far as I'm aware there are still no Linux viruses in the wild, so your chances of being infected are just about zero.

This may not always be the case, of course, but for the moment I don't think you need to worry.

The eicar.com test file is simply a small text file that manages to simulate a Windows virus, not a Linux virus, but to the best of my knowledge, there is no similar test file available for Linux.

You do still need to be careful of some other malign threats such as some trojans and things like phishing attempts, but those are, of course, more a problem of the user than the software.

---

### Post by JoAnn_Donaldson on 2016-05-30
Back in my Unix days, we wrote what we call a "Rabbit" program. Basically it was a program that created a child process then started the child process. This continued until there was no more memory for it to
spawn. The fun part was trying to kill all the process if you caught it early. Otherwise you had only once choice, shutdown and reboot. Not really a virus but similar. Then there are zombie files.

---

### Post by j2ee on 2016-05-30
> **ajgreeny said:**
> As far as I'm aware there are still no Linux viruses in the wild, so your chances of being infected are just about zero.

This may not always be the case, of course, but for the moment I don't think you need to worry.

The eicar.com test file is simply a small text file that manages to simulate a Windows virus, not a Linux virus, but to the best of my knowledge, there is no similar test file available for Linux.

You do still need to be careful of some other malign threats such as some trojans and things like phishing attempts, but those are, of course, more a problem of the user than the software.

I think Android is also a kind of Linux like Ubuntu, there are virus for Android, then why not Ubuntu can get infected too?

---

### Post by Habitual on 2016-05-31
> **j2ee said:**
> I google and saw people talking about EICAR. Base on my understanding EICAR is a DOS execute file so it cannot simulate a Linux virus, it just simulate a Windows virus. So anyway to test if a Linux virus can infect Ubuntu without any antivirus?

**Your understanding is wrong** on both counts. Nothing personal.
You got scroogled (screwed by google) or the results of using it.,
On Windows, in Order: 
[LIST]
[*]Bat 
[*]Com 
[*]Exe 
[/LIST]
the EICAR string can be in any document, so it's name isn't an issue, and it certainly is NOT a DOS executable.
[EICAR]("https://en.wikipedia.org/wiki/EICAR") is a Test or Sample File known (supposed to be) to every A/V.
The string can be utilized in a test on any Operating system that can read the file.

---

### Post by ventrical on 2016-05-31
> **Habitual said:**
> **Your understanding is wrong** on both counts. Nothing personal.
You got scroogled (screwed by google) or the results of using it.,
On Windows, in Order: 
[LIST]
[*]Bat 
[*]Com 
[*]Exe 
[/LIST]
the EICAR string can be in any document, so it's name isn't an issue, and it certainly is NOT a DOS executable.
[EICAR]("https://en.wikipedia.org/wiki/EICAR") is a Test or Sample File known (supposed to be) to every A/V.
The string can be utilized in a test on any Operating system that can read the file.

Yes.. for example CAVL (Comodo AntiVirus for Linux-Ubuntu) *will* detect EICAR over the network in realtime, either in a text file, static scan or real time scanning. So if there is known malware coming over the network the pop-up guard will alert. If you have a Windows XP hdd mounted to your Ubuntu install CAVL will detect if you try to copy or open a quarenteened file. 

Regards..

---

### Post by j2ee on 2016-05-31
> **ventrical said:**
> Yes.. for example CAVL (Comodo AntiVirus for Linux-Ubuntu) *will* detect EICAR over the network in realtime, either in a text file, static scan or real time scanning. So if there is known malware coming over the network the pop-up guard will alert. If you have a Windows XP hdd mounted to your Ubuntu install CAVL will detect if you try to copy or open a quarenteened file. 

Regards..

OK thanks I understand this part, but then why Android can get infected and having a good number of virus targeting Android but not Ubuntu? I need antivirus for android but not ubuntu?

---

### Post by ventrical on 2016-05-31
> **j2ee said:**
> OK thanks I understand this part, but then why Android can get infected and having a good number of virus targeting Android but not Ubuntu? I need antivirus for android but not ubuntu?

A lot of android devices are running ubuntu.kernels on ARM form factors, ie; RCA Voyager 7.  I am not sure if the linux/ubuntu type AV software will work. I can check it out. uh .. from what I know ubuntu desktops can be run in VMs on tablets so I think the AV software should work also.. but with some resources being taxed and perhaps performance being affected.

Enter snappy!

Soon snappy will be available for both tablets and desktops and the snappy repos will be vaulted for critical updates.  What you get in the aftermarket with non-snap/non-canconical will always be suspect.

Regards..

---

### Post by ventrical on 2016-05-31
> **j2ee said:**
> OK thanks I understand this part, but then why Android can get infected and having a good number of virus targeting Android but not Ubuntu? I need antivirus for android but not ubuntu?

Just downloaded AVG.  It correctly detected one malware installed by the vendor, the Unsecure setting of High Privlidge  mode (rooted) and USB Debugging in developer mode.

using kernel vesion 3.4.67 root@ubuntu-081 #1
Android Version 4.4.2


Regards..

---

### Post by ventrical on 2016-06-22
... and on a side note from CAVL (Comodo AntiVirus for Linux) if you have had it installed for over a year  you may have to perform this command:

```

./fix_rebuild_driver.sh

```
 in terminal. You may also have to check properties and tic off the box to make it executable (at least on trusty). This will give you real time access to malware coming in over the network. You can get that file here : 
[http://www.bondoffamily-net.com/~kinta-chan/techknow/DownLoad/DownLoad.html](http://www.bondoffamily-net.com/~kinta-chan/techknow/DownLoad/DownLoad.html)


It has detected malware ie; 
TroWare.VBS .Exploit
TroWare.JS.Agent

all this crap coming in over the network. Although these malwares are custom made for Windows OSes it is still interesting to know that these scripts can still be planted on your ubuntu install.

Regards..

---

### Post by SeijiSensei on 2016-06-22
From what I've read, there are no "[viruses]("http://www.androidcentral.com/help-my-android-has-malware")" for Android.  You can stupidly install an app that contains malware, but I suspect the number of such threats at the Google Play Store approaches zero.  Why would you install an app from anywhere else?  

Could you install an app that contains malware onto Ubuntu?  Of course you could.  That's why you should stick to packages in the official repositories, or in PPAs from people or organizations worthy of your trust.  

People migrating from Windows are used to downloading software from hither and yon.  Linux users rarely if ever need to do that.

---

### Post by ventrical on 2016-06-22
My point being is that most all web browser are exploitable with security flaws yet to be discovered. One cannot just lay down and think that 'not a malware will touch ubuntu/linux'. 

regards..

---

### Post by Habitual on 2016-06-23
> **ventrical said:**
> My point being is that most all web browser are exploitable with security flaws yet to be discovered. One cannot just lay down and think that 'not a malware will touch ubuntu/linux'. 

regards..
I think the real flaw is that people believe A/V keeps them "safe".
Malware != viruses

End Transmission.

---

### Post by HermanAB on 2016-06-23
Android is Linux with a broken security model, to allow people to install Apps with the swipe of a credit card.

Other Linux versions have proper security.  So toss your Android phone into the crapper, then relax and enjoy your Ubuntu system.

---

### Post by ventrical on 2016-06-24
> **Habitual said:**
> I think the real flaw is that people believe A/V keeps them "safe".
Malware != viruses

End Transmission.

But we still test. As the topic heading states: 'How to test if a Linux virus can infect Ubuntu without any antivirus?"

So the conclusion is:
1. EICAR *test* virus can be copied to an Ubuntu operating system.
2. CAVL effectively detects the EICAR test malware over the network (on access) and via it's manual scan.

It is an important case study for noob security ITs.

Regards..

---

### Post by Habitual on 2016-06-24
> **ventrical said:**
> But we still test. As the topic heading states: 'How to test if a Linux virus can infect Ubuntu without any antivirus?"

So the conclusion is:
1. EICAR *test* virus can be copied to an Ubuntu operating system.

2. CAVL effectively detects the EICAR test malware over the network (on access) and via it's manual scan.

It is an important case study for noob security ITs.
It was a Great Security Question from an IT "noob".

---

### Post by ventrical on 2016-06-24
Quoting the OP,

> 
I google and saw people talking about EICAR. Base on my understanding  EICAR is a DOS execute file so it cannot simulate a Linux virus, it just  simulate a Windows virus. So anyway to test if a Linux virus can infect  Ubuntu without any antivirus? 				


with the followup..

> 
<...As far as I'm aware there are still no Linux viruses in the wild, so your chances of being infected are just about zero.

This may not always be the case, of course, but for the moment I don't think you need to worry.

The eicar.com test file is simply a small text file that manages to  simulate a Windows virus, not a Linux virus, but to the best of my  knowledge, there is no similar test file available for Linux. ...>


..so I agree with you .. it was a great question and I was able to prove that a Windows MS-DOS textfile test virus (which is standard EICAR) was able to be copied and detected (on access) by a anti-malware program designed for linux/ubuntu (CAVL) so when I open nautilus file manager and open /Download where I have eicar, I  get the pop up guard. So it begs the fair question as to what else is getting through behind the scenes with users  that have no on access malware guard?:)

Regards..

---

### Post by ventrical on 2016-06-24
Here is the ubuntu official documentation on the matter.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Regards..

---

### Post by ventrical on 2016-06-24
> **j2ee said:**
> I google and saw people talking about EICAR. Base on my understanding EICAR is a DOS execute file so it cannot simulate a Linux virus, it just simulate a Windows virus. So anyway to test if a Linux virus can infect Ubuntu without any antivirus?

If you do decide to install a linux based AV suite I would suggest Comodo or open source clamav. It is in Ubuntu Software Center. If you install a program like Comodo with on-access real time guard you can download the clamav-testfiles from the USC, or terminal and you will notice the on access guard alerter engage on each of the test files. The test files are not real malware . They are designed to have a signature similar to a malware which is a false positive and that is known to trigger an anti-malware guard.

ClamAv is command line based and has no alerter  or on access guard.

---

### Post by Habitual on 2016-06-26
> **ventrical said:**
> They are designed to have a signature similar to a malware which is a false positive and that is known to trigger an anti-malware guard.

ClamAv is command line based and has no alerter  or on access guard.
ClamAV doesn't clean either. Delete or Quarantine.
This 'anti-malware guard' notification must be specific to CAVL?

"Windows test virus"? 
Eicar don't care about no Windows.

Have a Great Day!

---

### Post by ventrical on 2016-06-27
> **Habitual said:**
> ClamAV doesn't clean either. Delete or Quarantine.
This 'anti-malware guard' notification must be specific to CAVL?


AVG for  Linux also has the guard.(Thanks to VinDSL for his help with this) :)

> 
"Windows test virus"? 
Eicar don't care about no Windows.

Have a Great Day!

As I said the clamav-test files will be detected by the CAVL guard. If you use terminal and install them from the ubuntu-universe repositories:

```

sudo apt-get install clamav-testfiles

```

the CAVL guard will detect them as apt is trying to install them. There are six testfiles in all. It is rather remarkable what CAVL did with this. In the meantime it allows me to mount Windows hdds  that are infected and does a fairly thourough cleaning. If you have a test hdd that had another AV program for Windows and has quarantined  files on it CAVL will detect the quarantined malware.

It is a handy app for legacy malware control.;) So of course if you are using Wine or running Windows in a VM it is a good tool. In fact it will provide better protection for Windows in a VM than for Windows  running stand alone with an AV program on bare metal.


Regards..

---

