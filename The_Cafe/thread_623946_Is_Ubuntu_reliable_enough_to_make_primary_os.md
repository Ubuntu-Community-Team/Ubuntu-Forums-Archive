---
title: "Is Ubuntu reliable enough to make primary os?"
date: 2007-11-26
forum: The Cafe
---

### Post by valkyr47 on 2007-11-26
I just installed Ubuntu as a dual boot along with XP, and now im thinking of just getting rid of xp altogether in favor of Ubuntu.. i mean i just love the simplicity and free-ness of this OS.

Problem is im in the IT field, so my primary environment is a windows domain, and i run a lot of applications like VNC viewer and remote desktop, as well as rely heavily on email... 

is there a reliable email alternative to outlook and is there anyone out there who is also in IT and able to run strictly ubuntu?

---

### Post by TidusBlade on 2007-11-26
I run strictly Ubuntu, only keep Windows since my brother plays abit on it, but I dont use it. A good alternative to outlook would be thunderbird, or Evolution for GNOME/Ubuntu or Kmail for KDE/Kubuntu. You can use WINE to run these programs you need, or use the Linux alternatives, like in KDE I use a remote desktop program called Krdc and it works very well. 
Good luck on migrating ;)

---

### Post by bodhi.zazen on 2007-11-26
Yes. I have many systems, both servers and desktops, with Ubuntu as the primary OS.

They will be as stable or as unstable as you make them. By that I mean, LTS = stable = long term support. Other versions are stable enough, but I tend to upgrade with new versions.

If you are always updating and running the latest beta, expect some bugs.

---

### Post by phidia on 2007-11-26
While i'm not IT I've done quite a lot with linux over the years and haven't had a windows install for at least 4 years. Is there something specific missing from thunderbird or icedove that prevents it from being an outlook replacement? I hear a lot of complaints about outlook from friends doing office work-but I realize that's just my sphere of contacts.
For using other apps or even windows itself you could consider [xen]("http://www.cl.cam.ac.uk/research/srg/netos/xen/").

---

### Post by mellowd on 2007-11-26
Once ubuntu is configured correctly it's rock solid

---

### Post by valkyr47 on 2007-11-26
the biggest and most important thing would be being able to browse windows servers and seeing their content, as long as i could browse, create and delete files and folders from shared network resources on our servers, i can make the migration, which i want to do... so can you?

---

### Post by mellowd on 2007-11-26
You sure can.

Are you going to be in a AD enviroment or just a simple network?

---

### Post by TidusBlade on 2007-11-26
I can see other computers in my LAN using windows perfectly, but just a few configurations to Samba, like [here](http://ubuntuforums.org/showthread.php?t=202605) are needed for them to see you, but you can see them with no extra configuration ;)

---

### Post by valkyr47 on 2007-11-26
its a windows domain with several file servers, a print server and an FTP server

---

### Post by zach12 on 2007-11-26
YEP it will work

---

### Post by santana on 2007-11-26
Ubuntu is great, although some caveats,
1)
x86_64 is not fully supported in general(like adobe flash doesn't have x86_64) That is not ubuntu's fault. Still if you want that web content you will have to use the 32 bit version of ubuntu. 
2) 
if you are using windows or mac then consider that your i-tunes isn't going to work in ubuntu. Also certain apps like auto-cad don't run under linux. However, office thankfully is not an issue thank to open office. 
3)
I have been seriously impressed with ubuntu and its package management system. I think this is where it shines over other distros. Take away the package managment and its no better than any of the rest. but I do have to say the latest dist-upgrade from firesty to gutsy was wrought with problems. Its kind of tempered my enthusiasm for ubuntu a little.

try it out, install as a dual boot. I did this a year or so ago and haven't booted into windows since!

---

### Post by atlfalcons866 on 2007-11-26
ive been windoze free since may 07 =)

---

### Post by Craigus on 2007-11-26
Gutsy is my primary OS. If I need windows, I run XP or Vista as virtual machines under VMWare and Virtualbox. I haven't had any stability problems at all.

---

### Post by jernau on 2007-11-26
Absolutely, my school laptop is linux only and I haven't had any problems with it at all. I still have a windows partition on my home computer, but just for gaming.

---

### Post by retrow on 2007-11-26
> **santana said:**
> if you are using windows or mac then consider that your i-tunes isn't going to work in ubuntu.You don't necessarily require i-Tunes. There are several media managers available that do the same work as i-Tunes. If you are thinking about iPod connectivity, its far more simple in Ubuntu than it is on Widows or mac. iPod is mounted as another hard disc just like your flash drive. The names of files are garbled up though, but if you load you iPod through something like totem, you can see your compilation just like you' see it on iTunes. As an added bonus, you can even transfer files from your iPod to your hard drive without any hassles.

---

### Post by Ubuntu Warrior on 2007-11-26
I have been running Ubuntu Linux on my home Dell OptiPlex GX520 since Oct 2004 and have never switched back to Windows. I am kinda techie though and there were some rough patches along the way (helped through with all the amazing advice on these forums :)) A general rule I follow (sorry Ubuntu Tech Support) is to never do a dist-upgrade as 8 times out of ten it doesn't handle things very well. Copy all your data out, make a backup and re-install from CD/DVD/ISO. My Feisty install simply stopped functioning normally from a network perspective but thankfully Gutsy seems to have solved these network woes.

A great milestone for us was at work ... we are now the proud tech support team of around 60 Ubuntu Linux 7.10 (Gutsy) workstations which have been operating for about 6 weeks without a major hitch. Again there was some tuning along the way: Samba works slightly differently and smb.conf needed tweaking to get our smbldap stuff to function (eg. authenticating off our OpenLDAP server, etc.). We have just finished setting the systems to auto update every week with some cron scripts. We had finally laid our Microsoft network to rest at the beginning of this year so are now running our entire network (supporting just under 250 devices) off Samba.

I'm an avid supporter of open source solutions but would be the first to admit that it is easier to deploy commercial products in a corporate environment. However, the advantages are clear further down the road: we save HUGE amounts of cash on software licensing, we have no more tech support resources than when running commercial products (in fact there are many areas where we now do things a lot smarter and more effectively) and the solution is open allowing us to improve our business by putting our own ideas into practice.

---

### Post by fjgaude on 2007-11-26
I'm a graphic designer and can report that Ubuntu is reliable and stable, at least for the last four years. Few issues, certainly no more than with Windows or Mac.

Go for it.

---

### Post by rsambuca on 2007-11-26
> **santana said:**
> Ubuntu is great, although some caveats,
1)
x86_64 is not fully supported in general(like adobe flash doesn't have x86_64) That is not ubuntu's fault. Still if you want that web content you will have to use the 32 bit version of ubuntu. 


Wrong.  Why do people insist on writing this outdated and incorrect information?  Where did you get this information?

With Gutsy, you just go to a website that uses flash, and you are asked if you want it installed.  

Please desist with this outdated fud.

---

### Post by oneadvent on 2007-11-26
I am the IT Manger at The Listener Group in Gulf Breeze Florida. I use Ubuntu on my laptop and I haven't even had a reason to go to the desktop that was provided. I do periodically have to VPN or RDP for specific tasks, (our ODBC driver wont work in Linux.) But as for working on the AD and the shared drives it is easier under Ubuntu. Especially because there is a Linux server here that houses the database. I can ssh to that and work more efficiently than if I were on Windoze. Plus I can do somethings more securily than they  can, and faster.

As for the email question. The exchange server that we use doesn't work so well with Evolution but it is workable. The best idea for that is OWA. POP3 works fine with Evolution. Or thunderbird for that matter.

If you have any questions, I would be happy to answer them. 

Josh

---

### Post by teryowen on 2007-11-26
Definitely. especially if you already had it running under dual boot and it was fine, the more reason to.

---

### Post by thelatinist on 2007-11-26
Ubuntu is definitely stable enough; I find it far more stable and reliable than any version of Windows I've used in my 12+ years of Windows use.  I dual-boot with Windows XP, but I haven't booted into Windows in weeks, and I've even removed the delay in Grub so that it skips the boot menu entirely.  My only quibble with Ubuntu is that I've not yet found things to take up the time I used to spend in basic maintenance on Windows: Ubuntu just doesn't need it.

I'm not used to an OS that just works.  This is why I end up here on these forums.

---

### Post by A-Dog on 2007-11-27
I've been using VNC viewer on Gutsy for a couple of weeks and it works marvelously. :)

---

### Post by Offoffoff on 2007-11-27
Ubuntu the Great is ready for everything if You are normal person with normal hardware. Esp. Ubuntu is suitable in small offices for "printing" job (If there is no need for special Windows accounting programs). Or for internet-cafe (it is more bulletproof owing to its rare usage and proper user rights management).

---

### Post by thetimekeeper on 2007-11-27
I am primarily an economist, but I deal heavily in the IT field. I use Ubuntu as my primary OS and I was surprised that I could do it. I use Thunderbird for my email, and Quanta Plus for webwork, although I usually have to dual boot to XP or run it through VMWare server to do visual basic coding, graphics work and coding (Dreamweaver and Photoshop). I personally haven't found GIMP to be very useful, but that may just be me.

I'm lovin Ubuntu. I have my system customized and Compiz Fusion, and it's a lot of fun, not to mention the power of the terminal.

---

### Post by heatblazer on 2007-11-27
It depends, but if you ask me - yes. I have installed it on over 20 machines and it works. The only PC that crashed was mine and it was because of me being lame :)

---

### Post by dpj23 on 2007-11-27
The only true way to find out is to make your primary OS...  Once you do... You will find out that it will do everything that you can do in Windows...  Right now the only hold up is you...  The answers you want will come from day-in and day-out usage...

I had the same questions about a year ago... Always kept a Linux machine around... But, never was 100% committed to it since my laptop was running XP...  Then, I needed to install a larger hard drive in it...  And that's when I went 100% Ubuntu...  Now, if I need Windows I run a small 12GB XP virtual machine...

---

### Post by m.musashi on 2007-11-27
It's my one and only OS but it did take me a while to finally rub windows out. It was a liberating feeling though.

---

### Post by santiagoward2000 on 2007-11-28
It's stable enough for me! Although I couldn't yet get rid of Windows, it is already my primary OS.

---

### Post by sirdilznik on 2007-11-28
Ubuntu is absolutely reliable enough to be used as a primary OS (that's what I use it as).  IMHO Windows is the OS that **isn't** reliable enough for everyday use.

---

### Post by TheDilettante on 2007-11-28
Well, I can't resist congratulating Ubuntu either - I switched, almost on a whim, from Windows, just wholly deleted everything but my backed-up music.  I haven't had a problem yet.  iTunes DRM encoding is obnoxious, but you can get around that (SoundTaxi, if nothing else)...

I love it.  On Win my memory usage was 90% and my poor little Inspiron groaned when I used iTunes in conjunction with anything.  Hardware being unaffordable, Ubuntu seemed natural, and now I am at most at 30%.

---

### Post by mahousaru on 2007-11-28
Hee hee i've noticed a few people state their work.  I'm an IT contractor for a primary MS environment, but personally I try not too go near the stuff myself.  Had SuSE on my home server box for ages, but made the switch to nearly a full Ubuntu network at home apart from my XP gaming box when Gutsy came out. Working on my MCSE as it seems to be a prereq to get a job where I currently am, but I have to admit the idea to say I recommend Ubuntu whilst touting a MS cert is pretty amusing :)

---

### Post by toupeiro on 2007-11-28
Linux has been my primary OS for over a year.  Recently, it was made the sole "bare metal" OS on my primary PC.

---

### Post by amitst on 2007-11-28
Using Ubuntu for 8 months now on my office laptop and it really rocks. I have kept the Windows XP on my laptop for the following reasons,
- Need to change my Windows domain password regularly (no way provided by the company other than using a Windows system)
- Can't use a shared excel workbook through OpenOffice (tried with Excel through wine but no success).
- Can't logon to company's wireless network (Ubuntu detects the wireless card but the wireless network requires Windows domain username and password. Through Windows this can be done by selecting an option)

Other than the above I don't require Windows.

---

### Post by samwyse on 2007-11-28
I'm not convinced that Windows is reliable enough to make primary os.

---

### Post by samjh on 2007-11-28
Been my primary OS for a year.  Only 2 serious problems so far: one due to a hardware upgrade with an unsupported RAID chip, and another due to X.org update that broke my xorg.conf settings.

So, yes, it is stable enough to be a primary OS.

However, Windows XP also caused almost no problems for me too.

Take that how you will. :p

---

### Post by scorp123 on 2007-11-28
> **valkyr47 said:**
>  Problem is im in the IT field, so  ... so you shouldn't be using Windows anyway, knowing how insecure and virus-infested it is. (yes, that was sarcasm and not really meant in earnest :) )

> **valkyr47 said:**
>  is there anyone out there who is also in IT and able to run strictly ubuntu?  Right here. Linux user since 1996. Ubuntu user since it got first released in 2004. And I don't use anything from Microsoft. And I am very happy. The customers I mostly work for (e.g. banks and other companies with 'high-security' areas and extreme demands when it comes to reliability) don't like Microsoft either (at one customer everything Microsoft is outright banned! :lolflag: ). 

"Microsoft is to software what McDonalds is to gourmet cooking" (the source of this unfortunately escapes me at the moment ... I think this is from the "fortunes" program?) :lolflag:

---

### Post by nikolas68 on 2007-11-28
> **samwyse said:**
> I'm not convinced that Windows is reliable enough to make primary os.

:lolflag: that's a good one....my Vista Ultimate (that i haven't used in months) is soooo unstable that i wonder how people can cope with the stress!!!

---

### Post by smithman89 on 2007-11-28
I have been using Ubuntu for over a year as my personal desktop OS.  When i first installed it, my windows boot died, but i found ubuntu more than capable of being a replacement for it.

---

### Post by Magnes on 2007-11-28
I use Ubuntu as my primary os  at home for two years now. Don't see a reason why it couldn't be used as such.

---

### Post by quinnten83 on 2007-11-28
> **Ubuntu Warrior said:**
> I have been running Ubuntu Linux on my home Dell OptiPlex GX520 since Oct 2004 and have never switched back to Windows. I am kinda techie though and there were some rough patches along the way (helped through with all the amazing advice on these forums :)) A general rule I follow (sorry Ubuntu Tech Support) is to never do a dist-upgrade as 8 times out of ten it doesn't handle things very well. Copy all your data out, make a backup and re-install from CD/DVD/ISO. My Feisty install simply stopped functioning normally from a network perspective but thankfully Gutsy seems to have solved these network woes.

A great milestone for us was at work ... we are now the proud tech support team of around 60 Ubuntu Linux 7.10 (Gutsy) workstations which have been operating for about 6 weeks without a major hitch. Again there was some tuning along the way: Samba works slightly differently and smb.conf needed tweaking to get our smbldap stuff to function (eg. authenticating off our OpenLDAP server, etc.). We have just finished setting the systems to auto update every week with some cron scripts. We had finally laid our Microsoft network to rest at the beginning of this year so are now running our entire network (supporting just under 250 devices) off Samba.

I'm an avid supporter of open source solutions but would be the first to admit that it is easier to deploy commercial products in a corporate environment. However, the advantages are clear further down the road: we save HUGE amounts of cash on software licensing, we have no more tech support resources than when running commercial products (in fact there are many areas where we now do things a lot smarter and more effectively) and the solution is open allowing us to improve our business by putting our own ideas into practice.

I would like to know more about this. How did this implementation work and what was necesarry, How much knowledge of linux was needed. Stuff like that...
If you don't mind, may I pm you some time. I don 't have really in depth questions as I am not a techie (yet), but I am interrested in how linux would work in de workplace as an alternative to MS.

---

### Post by quinnten83 on 2007-11-28
> **amitst said:**
> Using Ubuntu for 8 months now on my office laptop and it really rocks. I have kept the Windows XP on my laptop for the following reasons,
- Need to change my Windows domain password regularly (no way provided by the company other than using a Windows system)
- Can't use a shared excel workbook through OpenOffice (tried with Excel through wine but no success).
- Can't logon to company's wireless network (Ubuntu detects the wireless card but the wireless network requires Windows domain username and password. Through Windows this can be done by selecting an option)

Other than the above I don't require Windows.

I don't know if this thread helps, but i finally got on the wireless on my school. With GG you don't have to compile the latest madwifi. iy might need the certificate though, But ask around, maybe the local IT can help.

[http://ubuntuforums.org/showthread.php?t=561994]("http://ubuntuforums.org/showthread.php?t=561994")

---

### Post by zaentzpantz on 2012-09-02
Based on experience over the past two years, I'd say definitely no. 
Windows is flakey and annoying, yes, but Ubuntu can give you really big problems.  
If you've got lots of spare time to get into the programming, fault fixing and bug finding then Ubuntu can be the primary os, but do make lots of regular backups.
I just use it on a small notebook as the applications I need are few and work ok. My main computer is now good old Windows ever since a disatrous Ubuntu update lost track of the graphics drivers.

---

### Post by coffeecat on 2012-09-02
Closed for necromancy.

@zaentzpantz, please look at the date of the previous post before posting to a thread. This thread had been slumbering for nearly **5 years**!

---

