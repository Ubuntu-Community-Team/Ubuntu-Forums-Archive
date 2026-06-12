---
title: "Do I have a virus?"
date: 2016-04-28
forum: Security
---

### Post by hermes5 on 2016-04-28
Hi. I downloaded a questionable video from a torrent site which when opened in VLC made the computer hang, but then the video closed. I deleted the file thinking whatever, I'm on linux and I didn't enter my password so no root access (right?). So over the last 2 weeks a bug which i noticed was firefox wouldn't pick up my keystrokes. Sometimes a restart would fix this problem. I thought it might be a firefox bug but when I went to upgrade firefox, immediatly after opening upp terminal I got this...

```
james@vulcan:~$ 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost        
james@vulcan:~$ susdsos 
```

Edit - As soon as I entered that code the keyboard again stopped working. To finish what I was saying, that command susdsos popped up in my terminal without me typing it, and after googling it I found no results, which I think is very strange.

---

### Post by gnusci on 2016-05-01
You got a hacker in your system, I think the best for you is clean reinstall.

---

### Post by BasiliusCarver on 2016-05-01
You can try to run a virus scan with Clam which is available through the aptitude package manager to verify your concerns.

ROOT NOTE: *If you want to scan all files you need to run this as root or else it won't have permission to read a lot of your files/directories.*

**To install:**
```
sudo apt-get update
sudo apt-get install clamav
```

**Update virus definitions (This gets the signatures from the web that Clam uses to identify bad code):**
You may get an error here about clamd.conf not existing.
You can install the clamav-daemon to rectify this if you want real time scanning otherwise ignore it.
```
sudo freshclam
```

**To do your first scan:**
This scan will start at / and recursively check the whole way up the directory tree (whole machine) and only show the infected files it finds.
```
sudo clamscan -ri /
```
[LIST]
[*]The -r flag means recursively scan the specified directory.
[*]The -i flag tells the scan to only output infected files.
[*]The / indicates the directory to start scanning from.
[/LIST]

---

### Post by hermes5 on 2016-05-02
Thanks for the replies. Installed clam and did a full scan, unfortunately picked up no infected files, however there were some files which I didn't have permission to scan, mainly located in /sys/module/. I might have to do a clean install but I can't afford to at this time. I need the laptop to work on. If anyone else has any ideas it would be really appreciated.

---

### Post by DuckHook on 2016-05-02
*Your thread has been moved to **Security** as the forum more suited to your issue.*

---

### Post by hermes5 on 2016-05-02
Thanks DuckHook.

---

### Post by BasiliusCarver on 2016-05-02
Ah yes, /sys could have been excluded to reduce the noise sorry.

Clean install is your best bet as gnusci recommended.

**However if you want to dig a little deeper into what's going on with this "susdsos" you can try the following (semi-advanced):**

[LIST=1]
[*]Check your hosts file for suspicious entries

*Reason to look: This output your terminal keeps spitting out is a collection of standard ipv6 host file entries.*
```
::1              ff02::2          ip6-localnet     vulcan
fe00::0          ip6-allnodes     ip6-loopback     
ff00::0          ip6-allrouters   ip6-mcastprefix  
ff02::1          ip6-localhost    localhost
```

Example from my /etc/hosts file:
```
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

View your hosts file by using cat:
```
cat /etc/hosts
```

[*]**Find out where susdsos is located on your machine:**
```
whereis susdsos
```

[*]**Inspect susdsos application**

If whereis gave you a file location (e.g. /usr/bin/susdos) then you can use strings to inspect the file.
Because the output can be quite long it is best to write the output to a new file.

Example (assuming susdsos was in /usr/bin), this will write the output of strings to a file called susdsos_strings.txt your home directory:
```
strings /usr/bin/susdsos > ~/susdsos_strings.txt
```

Then you can open the file in a text editor.
[/LIST]

---

### Post by DuckHook on 2016-05-02
Rather than repeat myself, [here]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") is a link to an old thread dealing generally with security and therefore relates to your situation. It's lengthy, but informative, and worth taking the time to read.

Yours is a recurring topic in security, so a short summary of what is in that thread:

Antivirus is next to useless in Linux. There are no known Linux viruses in the wild, which makes AV about as useful as a parachute on a boat. Moreover, Clam is notoriously unreliable and returns false positives in addition to its poor detection failure rate. But the biggest flaw of AV in Linux is that it gives users (and especially new users from Windows) a false sense of security, which leads to continued bad and lazy habits.

The critical element in security is user habits: good computing habits are essential; reliance on AV is foolish.

Re: your situation.

If I were you, I would assume that every keystroke is being recorded. It is *not* necessary for a cracker to have root access to do this (see [this]("http://ubuntuforums.org/showthread.php?t=2170638&p=12770607#post12770607") post). I strongly suggest that you reinstall. Better safe than sorry.

---

### Post by hermes5 on 2016-05-02
Ok thanks for your help. zzz terrible timing. Do I need to worry about files being infected by whatever this is within the system? By that I mean I have a bit of work on this laptop so I will need to back them up somewhere, but I don't want to port the thing over onto a fresh machine.

---

### Post by DuckHook on 2016-05-02
There are no absolute answers in security, so can't say your files are definitively OK. However the strong likelihood is that they are. Crackers don't try to go after everything; they go after the low hanging fruit. The biggest point of vulnerability is always the browser, so that is your main worry. If you stick to backing up just your data but not your cache or your configs you should come out of this fine.

---

### Post by hermes5 on 2016-05-02
> **DuckHook said:**
> There are no absolute answers in security, so can't say your files are definitively OK. However the strong likelihood is that they are. Crackers don't try to go after everything; they go after the low hanging fruit. The biggest point of vulnerability is always the browser, so that is your main worry. If you stick to backing up just your data but not your cache or your configs you should come out of this fine.

Ok thanks a lot for your advice. I think it's pretty interesting though, I thought using a linux distro would have made me a higher hanging fruit. I'm going to bring the computer into my university tomorrow, maybe some of the infosec guys might like to have a look at it. I guess I could post the results, but consider it solved if it pleases you.

---

### Post by DuckHook on 2016-05-02
> **hermes5 said:**
> ...I thought using a linux distro would have made me a higher hanging fruit...Well, I'd say no viruses in the world starts you out ahead of the game by a wide margin. :)

As my linked post explains, Linux isn't a magic wand. It starts out of the box arguably safer than the proprietary OSes, but *only if* the user actually bothers to take advantage of its strengths. No OS, no matter how well built, can make up for user laziness or bad habits. The OS at most contributes to, say, 5% of security. The user determines the other 95%. You've probably learned your lesson, but for others who may happen upon this thread, all bets are off if you insist on opening promiscuously torrented files or willy-nilly installing apps from outside the repositories. _Linux cannot save you from yourself_. No OS can.

If you must use risky files because of the demands of work or study, then do so on a separate non-production box inside a Virtual Machine. If you only have the one computer, at least use such files inside a well sandboxed VM. VM usage is beyond the scope of this thread, but the gurus in the Virtualisation forums would be happy to help you get started.
> ...consider it solved...I think we've beaten this one to death, so marking it solved will help others who happen upon this thread. To mark *solved* please use the Thread Tools above your initial post.

---

### Post by Habitual on 2016-05-02
Why would the "university 'infosec'" guys *care* exactly? 
Why did you run it 7 times on your computer? (facepalm)
Your opening post suggests you did, or was that a re-creation of "the scene of the crime"?

---

### Post by CharlesA on 2016-05-02
susdsos seems to be "events" in Spanish.

What would you want someone here to do?

---

### Post by HermanAB on 2016-05-03
Note that VLC is a horribly bug ridden program for which crashing is normal.

---

