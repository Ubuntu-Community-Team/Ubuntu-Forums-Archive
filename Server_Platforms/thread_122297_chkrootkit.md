---
title: "chkrootkit"
date: 2006-01-27
forum: Server Platforms
---

### Post by Peter76 on 2006-01-27
Hello, I've just installed chkrootkit on my server and ran it. At one point it says:

eth0: PACKET SNIFFER(/sbin/dhclient3[4480])
eth1: PACKET SNIFFER(/usr/sbin/dhcpd3[5332])
eth2: PACKET SNIFFER(/usr/sbin/dhcpd3[5332])
eth3: PACKET SNIFFER(/usr/sbin/dhcpd3[5332])

The rest of the tests turn out ok. Is this normal? I do have a dhcp-server running on the mentioned nics.

---

### Post by MJN on 2006-01-27
A Google search suggests it is indeed a very common 'false positive'...
 
But that's the problem with this sort of thing... how do you determine what *really* is a false positive... for *your* system? For all you know /sbin/dhclient3 could well have been compromised and whilst it's still performing your DHCP function it's also sniffing passwords and e-mailing them to somewhere in Russia.
 
No-one can confidently say it's common therefore can safely be ignored... To do so would make dhclient3 the obvious target of any malicious packet sniffer as per the above...
 
That's not much help really is it?!
 
Mathew

---

### Post by Peter76 on 2006-01-27
Well, some more weird things: I was just trying to set the dhcp-server up for static ip's, and it turned out there was a dhcpd.conf.swp file from last wednesday night; which means someone edited it and then something went wrong ( it was definitely not me ). The shitty thing is I just threw it away accidentally ( as well with my dhcpd.conf LOL ; first thing now is alias rm rm -i !!!! )
Now I'm quite new to this, but to me my ssh-server looks quite safe: wednesday night, it only listened on internal nics; and I ( think so ) have a strong password. It's also not listening on port 22 anymore.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=MJN]But that's the problem with this sort of thing... how do you determine what *really* is a false positive... for *your* system? For all you know /sbin/dhclient3 could well have been compromised and whilst it's still performing your DHCP function it's also sniffing passwords and e-mailing them to somewhere in Russia.[/quote]You have to code audit it at that point.  DHCP must be a layer-2 filtering application in order to do it's job.

---

### Post by Peter76 on 2006-01-27
And how do I do that????

---

### Post by LordHunter317 on 2006-01-27
Audit the code?  Download the source and audit it by hand to verify it's operation is correctly.  Good luck with that BTW, ISC' DHCP code is a buggy mess.

After you do that, you have to verify your binary is from that audited source: which requires a known-clean box to compile it on and compare checksums.  

It's not a realistic solution.  You don't go about addressing trojan risks that way usually.  You use an IDS, from the beginning, and known clean, trusted sources.

---

### Post by Oceola on 2006-01-27
If you've installed and are running the older .44 version you may want to try and download the 46 version form the Chkrootkit site and run it as a seperate. Place it in a different named directory and run the newer version from there, you may have to run Makefile and make sure you DL the three available files, the Makefile looks for things in the other files to double check.

You could also try and run Rkhunter, there's an update at their site and there's an rpm which will install without Synaptics. Does a fair job it may use alien but it doesn't appear to. It places itself in all the appropriate folders

I ran Chkrootkit .44 against 46 and kept getting an LKM notice, nothing definite, then ran chkrootkit --debug and it cleared up the false read.

Rkhunter never read the LKM and gave the system a clean bill of health

---

### Post by Peter76 on 2006-01-27
Thanks oceola, I'll give yor options a try

---

### Post by HJThis on 2006-01-28
Hello,Peter76

Just like to add you should also install
rkhunter to use along side chkrootkit

i think you can just 

sudo apt-get install rkhunter

then do sudo rkhunter -update

& to run a scan i use this here

sudo rkhunter -c --skip-keypress

Best of luck

---

### Post by towsonu2003 on 2006-01-28
what about running ethereal and looking what those interfaces are doing on their leasure time (while you're not working)? OP should be able to see whether anything is being sent out without his/her consent. not a space-saving and exact solution, but a starting point.

---

### Post by Peter76 on 2006-01-28
Thanks for the help again; I'll install rkhunter today. The sniffing is a very good idea; I'll do it with tcpdump though; is more space saving.

---

### Post by LordHunter317 on 2006-01-28
I should point out (and should have at the beginning) that running any sort of rootkit detecter on the system itself is silly.  You have to do it from a livecd.

---

### Post by MJN on 2006-01-28
Would it not suffice to merely run the detector from a read-only source (CD etc) containing the binaries and whatever databases it may need?

I must confess to only knowing the principles of rootkit detection so this could well be a naive question...

Mathew

---

### Post by LordHunter317 on 2006-01-28
No, you must reboot into a clean system.

---

### Post by HJThis on 2006-01-28
Hello,To all

@LordHunter317

Wow you are so right what's to stop someone from
just changing some settings in rkhunter so may i ask
how do you go about doing it with a Live CD please

can you post a how to or do you have a link
any help at all.

Best of luck

---

### Post by MJN on 2006-01-28
[quote=LordHunter317]No, you must reboot into a clean system.[/quote] 
Thanks for that comprehensive reply... all clear now! :???:

Seriously, can you explain to me/us why it cannot be run from, say, a CD-ROM that you 'trust'?

Mathew

---

### Post by LordHunter317 on 2006-01-28
[QUOTE=MJN]Seriously, can you explain to me/us why it cannot be run from, say, a CD-ROM that you 'trust'?[/quote]Because if the running kernel is compromised, then it doesn't matter that if the detection binaries are clean or not: they rely on the kernel to get their data, and a trojaned kernel can yield bad data.

A prerequisite for clean binaries means clean kernel, and that means a boot off a LiveCD or similar mechanism.

---

### Post by towsonu2003 on 2006-01-28
I will be repeating what others are asking but, how do you run chkrootkit / rkhunter from a livecd? wouldn't it check the integrity of the livecd filesystem but not the mounted harddisk? from what I see during scan reports, it looks at specific places (/something/somefile) for each rootkit / compromised configuration files. so if you run rkhunter from a live cd it will check /something instead of checking /media/harddisk1/something/somefile.

---

### Post by LordHunter317 on 2006-01-28
Mount the potentially compromised box's filesystem first, and both rkhunter and chkrootkit have a mechanism to tell them where to search.  I forget it off-hand, though.

---

### Post by HJThis on 2006-01-29
Hey,All

Yes 

@LordHunter317

Could you please post more info on this just
how would you go about doing this.

& do you use the Ubuntu Live-CD ????
i am so lost i have been on the net all day
trying to find info on just how to do this

Best of luck

---

### Post by MJN on 2006-01-29
Thanks LordHunter; makes sense now.

---

### Post by HJThis on 2006-01-29
Hello,All

Could someone please help me with this going nut's here
how do you use a Live-CD to scan with chkrootkit & rkhunter
do i use an Ubuntu??? Live-CD if so how do you go about this

please anyone at all

Best of luck

---

### Post by chrisTGc on 2006-02-08
Hullo,
Thanks everyone for posts seems what i was concerned about where false positives anyway so ille relax.
HJThis,it seems everyone is fixed ok and not reading this thread but i hope u still are.Some answers are;No you dont have to use the Ubuntu live CD.Maybe best is Insert live CD which has chkrootkit,rkhunter and also clamav already incorporated.Insert is available from [http://www.inside-security.de/download_en.html](http://www.inside-security.de/download_en.html) and is a 50MB ISO file ready for burning to CD.You will prob need broadband or some patience if on dialup if you decide to try this.
Disregard this next bit if you know but just in case;an ISO is not a data file and it is best NOT to insert the blank CD first.Download the ISO into Ubuntu and simply right click the ISO,follow the dialogue into CD burning and then insert the blank CD.Saves making coasters like i did.
Inserts easy enough to use and v1.35a seems pretty much upto date.Any probs post again and i will watch out for it. 
Best Wishes Chris.

---

### Post by Oceola on 2006-02-09
I'm curious after reading the necessity of a remote LiveCD application of Chkrootkit or any other, if the removal from the system is necessary. Why not a seperate area or folder setup, hidden from the normal tree and used as a standalone. Leaving one version in place as a decoy and then allowing another version to function on an unscripted call or allowing another to be toggled through a different method.

I'm also curious how you use a liveCD to become root since root is required for the priveledges of rootkithunter.?:-k

---

### Post by LordHunter317 on 2006-02-09
[QUOTE=Oceola] Why not a seperate area or folder setup, hidden from the normal tree and used as a standalone.[/quote]**Because if the kernel is corrupted, you still lose.**

Even if you had a totally second install on the disk that's normally unmounted, the attacker could mount it and compromise it.  You have to use known-good binaries, and that means a CD.

---

### Post by chrisTGc on 2006-02-09
Thats right,CD runs of its own Kernel and is READ ONLY.

With a live CD you are usually logged in as root or can become so via sudo.Using the Insert GNU/Linux live CD the Ubuntu root partition is scanned with rkhunter with;
#sudo rkhunter --rootdir /mnt/hda3/ -c

hda3 being the Ubuntu root on this machine and not forgetting to use mount app,bottom right hand corner to mount the partition in the first place.chkrootkit would be used;
#sudo chkrootkit -r /mnt/hda3/ 

Best wishes Chris.

---

### Post by Oceola on 2006-02-11
Lord Hunter & ChrisTG Thanks for an answer.
I'll give it a try and see if there's any differenece.
My luck I'll find the Thundering Horde..
Take Care
:)

---

### Post by chrisTGc on 2006-02-12
[QUOTE=Oceola]Lord Hunter & ChrisTG Thanks for an answer.
I'll give it a try and see if there's any differenece.
My luck I'll find the Thundering Horde..
Take Care
:)[/QUOTE]
Haha.Good luck and sure you will be ok.Had to deal with a thundering hoard myself but on a friends machine.My friends machine was running Windows,(so can always be worse),16 viruses and 600+ items of spyware with 20 of those rather more than just cookies.Put friend Natalie's machine on a dual boot with Feather GNU/Linux.

Updated Insert live CD myself to the current v1.35a from v1.2.18.chkrootkit and rkhunter from there say clean here.Just confirms the 3 items from same tests in Ubuntu are false positives.

Best Wishes Chris.

---

### Post by Road on 2006-03-01
This is a known false positive. I checked the debian bug reports.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343523](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343523)

I would not worry about it, because it would do the exact same thing on a prestine machine.

---

### Post by feld on 2006-03-02
nm...

---

### Post by towsonu2003 on 2006-03-02
[QUOTE=feld]nm...[/QUOTE]
I know what you wrote :PpP ;) I agree that md5sums would be different in two packages compiled in two different machines. I don't know why I agree though ;)

---

