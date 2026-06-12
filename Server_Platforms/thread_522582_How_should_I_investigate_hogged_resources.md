---
title: "How should I investigate hogged resources?"
date: 2007-08-10
forum: Server Platforms
---

### Post by boweeb on 2007-08-10
_Background_:
My home server is a fun side project for me. It's an old gateway (PII 350Mhz w/100Mb RAM) running 6.10 server. I've managed to set up a LAMP server, samba, jinzora, torrentflux, trac, movable type, webmin, cacti, base, sugarcrm, phpbb2, and a nexuiz dedicated server. I admit that I don't use all of these but I've really enjoyed playing with them and slugging through their installs while scouring forums and documentation figuring it all out.

But I've hit a wall. My memory suddenly became brimming full this morning. Top tells me that I have 10 apache2 processes running taking up %98 of my available memory. At 7am my server was happy and responsive - a couple hours later it took 15 seconds for typed characters to show up on screen. I tried rebooting with no results.

What was I doing? I was working on jinzora trying to move my media to another folder... and I finished. I was done, it worked fine, and I tested a few files.

_So my question is:_
How do I go about researching this? What's my next move? I've never tried to tackle a problem in this realm before.

---

### Post by Mr. C. on 2007-08-11
That 100Mb is being stretched very thin... this is too little memory for what you are trying to do.  Your delays are likely being caused by the VM system thrashing  You're seeing swap delays, as that system struggles to free up pages.  And with that old 350mhz system, its likely the disk interface is very slow as well, so you're not going to win this battle.

Best of luck,
MrC

---

### Post by boweeb on 2007-08-11
You have a convincing argument. However that leaves two questions:

1. Is it normal to have 10 apache processes?
2. It ran fine one minute then was bogged down the next. Why has my memory (of which I'm very aware is extremely low) only now become a problem (and so suddenly)?

As far as I know, very few of the programs on my list actually do anything unless I'm accessing them (eg nexuiz-server). At least that's been my theory - the one-at-a-time theory. I've actually been perplexed that I made it this far.

---

### Post by netlogic on 2007-08-11
Yes, it depends on the distro. Since, the memory size of apache is small. It runs in multiple process, so clients don't have to wait. If this is an intranet server for your home for one or two people, you can reduce the number of apache server running by modifying your apache config file.

---

### Post by netlogic on 2007-08-11
Oh, your sever isn't so bad... You probably need to yank some packages out that you don't need. If you want to learn, you might have a better chance if you redo your kernel. Also, check your ram for one or two faulty chip. Since, this is an old machine make sure you set your memory speed to the lowest speed of the ram stick you have installed. Faulty hardware can cause CPU to spike.

My home server is 233mhz, 96megs of ram with 800gigs (500+320) drive. It is running samba, bind, apache, php, ssh, ftp, squid, multiple screen sessions, postfix, shorewall, and fail2ban. I still have 2megs free. ;) I am jealous. You have a speed demon for your home server.

---

### Post by koenn on 2007-08-12
> **boweeb said:**
> 
Top tells me that I have 10 apache2 processes running taking up %98 of my available memory. 
_So my question is:_
How do I go about researching this? What's my next move? I've never tried to tackle a problem in this realm before.
try to find out what's keeping apache busy. 
Check apache's logs,
and see how many active connections it's maintaining , eg with netstat
```
netstat -nap --tcp
```
look for apache and /or connections to port 80
add -c option for a continouos refresh : netstat -napc --tcp

---

### Post by foxylad on 2007-08-12
I use vmstat to watch server load, it shows IO, swap, memory and processor resources. I once wrote a python script that watched the output of vmstat for a low idle figure, and then did a ps to see what was taking the resources:

```
import sys,os,smtplib

limit=0.1

try:
	vmstat=os.popen('vmstat -n 10','r')
except:
	print "Cannot open pipe to vmstat"
	sys.exit(1)

count=0

msg=''

line=vmstat.readline()
while line:
	count+=1
	if count==1:
		vmstatLine1=line
	if count==2:
		vmstatLine2=line
	if count>3:
		words=line.split()
		if int(words[14])<50:
			# CPU usage is high - take a snapshot
			try:
				ps=os.popen('ps -eo pid,ppid,user,pcpu,args --sort -pcpu','r')
			except:
				print "Cannot open pipe to ps"
				sys.exit(1)
			msg+=vmstatLine1+vmstatLine2+line+'\n'+''.join(ps.readlines())+'\n'
			ps.close()

		else:
			# CPU usage is lower - send email if we have a message
			if len(msg):
				server=smtplib.SMTP('localhost')
				server.sendmail('you@your.domain','g.fawcett@gmail.com','Subject: psmon output\n\n'+msg)
				server.quit()
				msg=''

	line=vmstat.readline()

vmstat.close() # Doesn't seem to work

```

You may not need this if the load is always high - just the ps bit.

Good luck!

---

### Post by boweeb on 2007-08-13
A monkey wrench has been thrown into my research. My server's responsiveness has returned! My memory is still hogged but I suspect that it was before the responsiveness issue came up. Nothings really different, I just left it alone for a few days. Perhaps after I told jinzora to recreate the media database (35+ gb of mp3s), even though it appeared to work right away, it was still querying id3 tags in the background. Then again shouldn't something have looked suspicious in top? Just a theory.

Anyway, since I no longer seem to be afflicted, maybe the best thing to do is analyze logs. Thanks guys for all your posts. Any suggestions for making it easier to diagnose if it happens again? Or thoughts on analyzing logs?

> If this is an intranet server for your home for one or two people, you can reduce the number of apache server running by modifying your apache config file.
I'm having trouble finding that option in the config file. You're talking about apache2.conf, right?
> You have a speed demon for your home server.
That's one of the things I really like about linux - you can always find something useful to do with just about any hardware.
> ```
netstat -nap --tcp
```
look for apache and /or connections to port 80
```
tcp6       0      0 :::80               :::*               LISTEN     15815/apache2
```is the only line with apache in it.
> Check apache's logs, and see how many active connections it's maintainingShould I grep this somehow? I'm having trouble interpreting it.
> I use vmstat to watch server load... You may not need this if the load is always high - just the ps bit.
Neat script, but it gives me a "unable to open X server" error. Would it be much trouble to create a CLI version?

---

### Post by netlogic on 2007-08-13
You want to play with these settings in your apache2.conf

# prefork MPM
# StartServers ......... number of server processes to start
# MinSpareServers ...... minimum number of server processes which are kept spare
# MaxSpareServers ...... maximum number of server processes which are kept spare
# MaxClients ........... maximum number of server processes allowed to start
# MaxRequestsPerChild .. maximum number of requests a server process serves

I don't know your needs, but it seems like a busy person. Why not just do this...

StartServers         1
MinSpareServers      2
MaxSpareServers     5
MaxClients          5
MaxRequestsPerChild  0

You probably could save about 1/2meg by removing few getty too. I am assuming this is a server, so yank out things you don't use.

---

### Post by foxylad on 2007-08-13
It **is** a CLI program. I've only run it from the CLI (my server doesn't have X-Windows) so maybe something weird is happening if you run it from the desktop. Try running it from a terminal if you didn't already.

---

### Post by lavinog on 2007-08-14
> 2. It ran fine one minute then was bogged down the next. Why has my memory (of which I'm very aware is extremely low) only now become a problem (and so suddenly)?

It could be that your server was under attack by a hacker.
You may need to check your logs.
Every now and then I get a hacker that is trying to scan everything available to the internet...although they don't get anywhere it still consumes resources. Many of times they try and use multi-threaded port scans that really do a number on your computer

look into the error logs (you may have to enable logging first)

next time it bogs down do netstat

---

### Post by netlogic on 2007-08-14
I can't make definite assumption about the situation without looking at his logs, but I don't think it is DOS attack. It might appear that way in the log if his torrentflux isn't properly configured. Since, he is low on ram, he might need to run things like torrentflux in the lower process priority. I am not sure how Bitornado (backend) handles caching of torrent connection, but I bet it is sucking up a lot of ram during many concurrent connections.

---

### Post by lavinog on 2007-08-14
> **netlogic said:**
> I can't make definite assumption about the situation without looking at his logs, but I don't think it is DOS attack. It might appear that way in the log if his torrentflux isn't properly configured. Since, he is low on ram, he might need to run things like torrentflux in the lower process priority. I am not sure how Bitornado (backend) handles caching of torrent connection, but I bet it is sucking up a lot of ram during many concurrent connections.

I agree, torrents can be memory hogs too.
It could also be why the problem seemed to go away.

---

### Post by boweeb on 2007-08-18
No dice on the torrent theory. I hadn't torrented for three weeks until last night. The three weeks overlaps my original problem and the server held up just fine last night.

Everything seems back to normal and I'm still leaning towards my theory that jinzora was cataloging.

Since it doesn't really seem possible to diagnose what happened, future posts should probably concern what to do if it happens again or how I might be prepared for a next time.

(Thanks again for all the responses)

---

