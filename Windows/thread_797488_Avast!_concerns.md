---
title: "Avast! concerns"
date: 2008-05-17
forum: Windows
---

### Post by the8thstar on 2008-05-17
Hello all,

I installed and ran Avast! (antivirus for Linux) just for the heck of it, with the latest definitions.

Well, the results are concerning me. After a long scan, it gave me a list of about 150 files and folders, with a choice of delete or quarantine.

Most of the files found are located on my Windows partition, but some were also found in / and in /home. I can access Windows from Ubuntu (with ntfs-utils) and vice-versa in Windows (with ext2fs). The oddest thing was that nothing was found when running Spybot (anti-spyware) and AVG (anti-virus) in Windows with the latest definitions in both.

For the record, I use Firestarter (iptables) in Ubuntu, AVG, Peerguardian and Spybot in Windows Vista and I have a hardware firewall on my modem too with NAT set to "on". I also have a bunch of addons in Firefox (on both systems) that supposedly protect my privacy.

So, here are my questions:

[B][COLOR="Blue"][B]1. Is Avast! reliable? 
2. If so, why didn't Spybot or AVG pick up anything?
3. Should I reinstall the system?
4. Am I ever going to be free from the badware???[/B][/COLOR][/B]

---

### Post by NewDisciple on 2008-05-17
What is being identified by Avast?  If I remember correctly, Spybot itself will create a false positive with other security programs.

---

### Post by -grubby on 2008-05-17
> **NewDisciple said:**
> What is being identified by Avast?  If I remember correctly, Spybot itself will create a false positive with other security programs.

Yah..they're probably false positives__________________

---

### Post by rune0077 on 2008-05-17
For a funny test, download Avast for Windows as well and then run it in Windows - would be fun to see if it detects the same files as it did from Linux. 

Either way, I used to use Avast when I used Windows, and I always found it very reliable and it kept my system Virus free (together with Spybot). Still, if you have a commercial anti-virus program, I would probably trust that instead, at least if it's one of the "big ones".

---

### Post by the8thstar on 2008-05-17
> **NewDisciple said:**
> What is being identified by Avast?  If I remember correctly, Spybot itself will create a false positive with other security programs.

I can't tell because I closed the Avast window and haven't tried running it again since. All I can remember is pagefile.sys (Windows) and several entries in /dev/* and /home/*. But there were far more than that unfortunately :(

---

### Post by the8thstar on 2008-05-17
> **rune0077 said:**
> For a funny test, download Avast for Windows as well and then run it in Windows - would be fun to see if it detects the same files as it did from Linux. 

Either way, I used to use Avast when I used Windows, and I always found it very reliable and it kept my system Virus free (together with Spybot). Still, if you have a commercial anti-virus program, I would probably trust that instead, at least if it's one of the "big ones".

Good call. I'll try that.

---

### Post by jrusso2 on 2008-05-17
All of them seem to give you false alerts.  I always investigate before I delete or quarantine.

I have not seen Avast give more false alerts then the others like AVG and Avira.  Avira seems to give the most false alerts but it has the highest detection rates.  High detection rates will often give false positives.

---

### Post by Jiraya on 2008-05-17
> **rune0077 said:**
> For a funny test, download Avast for Windows as well and then run it in Windows - would be fun to see if it detects the same files as it did from Linux. 

Either way, I used to use Avast when I used Windows, and I always found it very reliable and it kept my system Virus free (together with Spybot). Still, if you have a commercial anti-virus program, I would probably trust that instead, at least if it's one of the "big ones".

I'm not sure about that. We have McAfee Viruscan Enterprise at my work. Sometimes people gets viruses (bankers, principally) that Viruscan don't remove (even identify as virus), but the symptoms don't lie. We then have to install and update avast! and run a boot scan to remove the infections.

[Linux Archive]("http://www.linux-archive.org")

---

### Post by rune0077 on 2008-05-17
> **Jiraya said:**
> I'm not sure about that. We have McAfee Viruscan Enterprise at my work. Sometimes people gets viruses (bankers, principally) that Viruscan don't remove (even identify as virus), but the symptoms don't lie. We then have to install and update avast! and run a boot scan to remove the infections.

McAfee is crap. If you want a good virus scanner, check out tests done on somewhat respected sites (like PC World or some such), and take that as a guide. McAfee rarely does very well on those. Bit defender and Bullguard seems to be really good.

---

### Post by Jiraya on 2008-05-17
> **rune0077 said:**
> McAfee is crap. If you want a good virus scanner, check out tests done on somewhat respected sites (like PC World or some such), and take that as a guide. McAfee rarely does very well on those. Bit defender and Bullguard seems to be really good.

Hmm... I've never heard about that Bullguard. I'm just realizing that I need to update myself a bit :)

[Linux Archive]("http://www.linux-archive.org")

---

### Post by smoker on 2008-05-18
> **the8thstar said:**
> So, here are my questions:

[B][COLOR=Blue][B]1. Is Avast! reliable? 
2. If so, why didn't Spybot or AVG pick up anything?
3. Should I reinstall the system?
4. Am I ever going to be free from the badware???[/B][/COLOR][/B]

what makes you think you have a virus, is your computer acting peculiar/unusual or sometwhat out of the ordinary?

in reality, good surfing and downloading habits are a more reliable way to avoid viruses than most antivirus apps. if you think you have a virus (in windows) do an online scan with this:
[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)
and this:
[http://onecare.live.com/site/en-us/default.htm](http://onecare.live.com/site/en-us/default.htm)
do the free scans, don't download demos or trials!

i wouldn't reinstall the system only on the say-so of some application, not without confirmation from multiple other sources, and only if that was a last resort!

---

### Post by aimpau on 2008-05-20
I used to use avast in XP SP2. They do have low false reports occurences however, as we know that linux's files are scripted in such a way that a "natively" windows AV would detect as something malicious.

I had an experience where in I have a file created in such a way it would patch a certain .dll. aVast would always detect is as semi-threat.

if you're still concerned, go here:
[www.virustotal.com](www.virustotal.com)

and check out the file.

---

