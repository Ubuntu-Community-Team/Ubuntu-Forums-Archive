---
title: "help"
date: 2007-08-19
forum: Windows
---

### Post by Hmarroqu on 2007-08-19
now im not a big fan of windoze but i figure i can ask this community since i trust in you all the most and ubuntu makes me happy, id like to ask those windoze users out there what kind of protection they use for it.  i have to use win and need to keep it clean from all those ITD's out there.  any suggestions?:confused:

---

### Post by aysiu on 2007-08-19
The best protection is using a limited user account most of the time and keeping a separate administrator account (that you rarely log into) for a few administrative tasks.

---

### Post by Dr. C on 2007-08-19
Here is what I do

1) Get a router and set all the ports to "stealth" or "drop packets silently", they make great hardware firewalls and are cheap under $50. If that router has wireless disable the wireless until one can properly set up the wireless security. Alternatively a GNU / Linux box with two nic cards can serve as a the router firewall. I actually have both. A router that connects to my DSL modem, the Ubuntu machine has one nic connected to the route and the internal nic is connected to a switch  where the Windows machines can plug into. Also any virtual machines running on the Ubuntu machine are attached to the internal nic. 
The main thing to keep in mind here is to **never** attach an unprotected and unpatched Windows machine directly to the Internet. It can be compromised before one even gets a chance to download the service packs and security patches to secure it. Early Windows XP before Service pack 2 are well known for this. 
If you really need to connect a Windows system directly to the Internet, for example a laptop while traveling,  I would  only try this  with a good software firewall for example [http://www.zonealarm.com]("http://www.zonealarm.com"), after the system that is completely patched  up to date, and with a version of Windows that is currently supported for security patches by Microsoft. 

2) Get  an Anti Virus. Before paying for a subscription consider these options:
a) Does your ISP provide this? Mine, Telus,  does at no additional charge for up to 5 computers. Works with Windows 2000 and XP
b) AVG Free. [http://free.grisoft.com/]("http://free.grisoft.com/")This is free as in beer, but limited to one computer for home use. One good thing about this is that it works on older versions of Windows such as Windows NT4. I use it on a Windows NT4 box that will not run my ISP's anti virus. The is also a GNU / Linux version.
c) ClamWin. [http://www.clamwin.com/]("http://www.clamwin.com/")This is only a scanner no real time protection, but it is FLOSS. A good choice for the occasional Windows user. 
One thing to keep in mind here is that the penguin does not get infected with Windows Viruses but is very much a carrier of these infections.  So it is very important to scan GNU / Linux systems particularly Samba shares for Windows viruses  in a mixed environment. 

3) Get more than one anti-spyware scanner and scan regularly. I use both Spybot Search and Destroy [http://www.safer-networking.org/en/download/]("http://www.safer-networking.org/en/download/") and Ad-Aware [http://www.lavasoftusa.com/]("http://www.lavasoftusa.com/") I suggest more than one since for legal reasons / threats they may not detect all adware. It is also best if at least one of the anti-spyware providers is based outside of the United States of America for the same "legal" reasons 

4) Keep the system up to date with the latest security patches etc. This applies to any OS not just Windows. 

5) Keep the Spam out. I use Thunderbird on Ubuntu for may email. It has an excellent bayesian anti spam filter that can be trained not only on spam but on viruses also. Popfile [http://popfile.sourceforge.net/]("http://popfile.sourceforge.net/")is also an excellent tool and works with any mail client. I have caught viruses with a well trained Popflie before the major anti virus companies. The virus came from a source that was supposedly protected with a commercial anti virus.

6) Finally I would use common sense there is no need download software form dubious sources, open every attachment, click on every .exe etc. Again this applies to any OS not just Windows.

---

### Post by darksong on 2007-08-19
The above Post made some very good suggestions. Rember to keep your windows up-to-date. AVG free or Avast anti virus are both very good free anti virus programmes. ([http://www.avast.com/index.html](http://www.avast.com/index.html)) Keeping either windows firewall or another firewall enabled is also a very good idea in windows and linux. I suggest using Comodo firewall which is free, and doesn't bug you to upgrade to any commercial software. ([http://www.personalfirewall.comodo.com/](http://www.personalfirewall.comodo.com/)) I also recomend using CCleaner - its not a secuirty application but it helps keep crap and unused files of your PC, adware 2007 will take cookies as adware and make you think your PC has a toone of adware on it - run this and it will get rid of cookies temp files ect and you can get a true count on adware. ([http://www.ccleaner.com/](http://www.ccleaner.com/))

I also advise downloading AVG anti spyware - it provides real time proection against adware and spyware - which i belive lavasoft adware 2007 free does not do.

---

### Post by smoker on 2007-08-19
the above suggestions are all great, but i would also stress to make uptodate regular backups of all your crucial data. a bad viral infection, or hardware failure, is less of a major setback if you know all your crucial data is safely backed up.

best of luck.

---

### Post by digital_exhaust on 2007-08-19
All really good suggestions.. but one important question needs to be answered before anyone can really help.... 

What version of Windows are you running? 

If your on XP, everything said above is great. I would however add [SuperAntiSpyware]("http://www.superantispyware.com/") to the list of free but very good applications. I have seen better results than those with SpyBot.. unfortunately it just doesn't keep up anymore and is basically useless at this point... sad, it was a great antispyware app for a long time.... 

If your using Vista... and you can flame me for this if you want, but understand I have been using it daily since the early beta builds, and it's completely different than any other Microsoft OS (any OS, really)... Windows Defender actually works, and UAC is a HUGE step in the right direction. Contrary to all the BS you'll hear about disabling it is exactly that... BS. Leave it enabled, install your programs and apps *correctly* and you won't have problems with it. 

My recommendation for keeping a Vista install clean is this. Run behind a router and  use the Vista firewall, it works fine, and blocks traffic in both directions unlike XP's firewall. Be sure your router is configured correctly. Let automatic updates do their thing, or have Vista notify you, whatever makes you happy... but just keep it updated. [CCleaner]("http://www.ccleaner.com/") is great, and SuperAntiSpyware applies here as well. As far as A/V is concerned.... AVG and Avast! are alright for "free" solutions.. but if you want an A/V that is lightweight and very reliable, [NOD32]("http://www.eset.com/") is worth every penny and more. Automatically updates every hour, and is so light on resources that you won't even know it's there... 

That's it. Vista, believe it or not, really does a fairly good job of taking care of itself. 

Hope that helps....

---

