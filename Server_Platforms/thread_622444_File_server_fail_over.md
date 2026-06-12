---
title: "File server fail over"
date: 2007-11-24
forum: Server Platforms
---

### Post by killerdragon on 2007-11-24
Lets say that I have 2 file servers, FS1 and FS2. They are set to rsync to/from each other, so each one has the same data the other has. And if one is updated the other is too.

This is going to sound stupid, but its the best way I can think of what I want to accomplish. (I will list what I am trying to do at the bottom)
Is there a way to tell Apache to use FS1 to grab the documents, and if FS1 is ever down then grab the documents off of FS2?

Why would I want do this?
I want to setup a redundant file system for when/if I upgrade hard drives. Sure I would always have to buy twice the size, but no outages.
Lets say I notice my HD space to start to fill up, I can bring FS1 down, install the new hard drive, wait for rsync to do its thing, then take down FS2 and upgrade that one, then rsync will run in FS2 and the servers are happy again. Goal in mind: Very little to no downtime.

---

### Post by prodezigner on 2007-11-24
Not the answer your probably looking for... but... one word one letter... RAID 5...

LOL

This that your asking is way too complex for me. I'm not the greatest sysadmin, but I know enough to get around. Plus with RAID 5 (use SATA drives) you can get hot swappable trays for your 5.25" bays. And you eliminate one whole computer doing this.

---

### Post by killerdragon on 2007-11-24
> **prodezigner said:**
> Not the answer your probably looking for... but... one word one letter... RAID 5...

LOL

This that your asking is way too complex for me. I'm not the greatest sysadmin, but I know enough to get around. Plus with RAID 5 (use SATA drives) you can get hot swappable trays for your 5.25" bays. And you eliminate one whole computer doing this.

That might be an option if I was running SATA but every computer I have uses IDE (expect for one which is a personal machine).
Nothing wrong with IDE, I have PLENTY of harddrives :P.

---

### Post by koenn on 2007-11-25
the sollution you describe is a fail-over cluster. A cluster is a group of servers (in your case : FS1 and FS2) that are identical, and present themselves as 1 machine (eg 'FS'). The nodes in a cluster check each other regularly, and if one node is down, the other takes over. Because the other hosts on the network only see 'FS', and not FS1 or FS2, this is completely transparant.


I suppose you can mimic this behaviour, eg with a script that, at regular intervals, checks that FS1 or FS2 are online, and react if 1 is down.
pseudo / concept code


```
while true; do
    sleep 30 ;
    if ping -c2 FS1 | grep "bytes from FS1" ; then
            # FS1 is  online
            # procedure to use FS1 goes here 

    elif ping -c2 FS2 | grep "bytes from FS2" ; then
            # FS2 is  online
            # procedure to use FS2 goes here 
    else
            #both FS1 and FS2 are down. Now what ?
    fi
done

######
# you need a procedure to let apache use a share on FS1 *or* FS2,
# eg do a 'find and replace' with sed, and reload the config
sed -i s/documentRoot=Something/DocumentRoot=SomethingElse/ path/to/apache.conf
/etc/init.d/apache force-reload

## or replace the entire conf file
if FS1 is online
     cp apache.conf.FS1 apache.conf
    /etc/init.d/apache force-reload


## or you can mount the share on the fileserver that is online
umount /var/www
smbmount //FS1/share /var/www

```

This needs work : eg 
* when FS1 is online, and 30 seconds later the script finds that FS1 is (still) online, you don't want to change anything ; the procedure to switch to FS2 should only be executed if apache is using FS1 and FS1 goes down - you need to figure out a test for this. 
* 30 sec may seem long, but you need to allow at least sufficient time for ping to time out if a server is down + the change to the other server + restart apache to be executed
* you'll need to test and work around some other problems, eg I don't know what happens to apache if /var/www suddenly disappears

I'm just making this up as I go - it's the direction I'd search in if this were my problem ....


---
yet another way of switching between FS1 or FS2 is to use your DNS server or /etc/hosts  (eg. use sed or cp to modify/replace  /etc/hosts or the DNS zone file), eg 
- use 'FS' as generic hostename  for your fileserver (eg in apache config or smb mount statements, ...)
- let FS be an alias for FS1  OR  FS2  depending on which one your script finds 'online'  | let 'FS' point to <ip address of FS1> or <ip address of FS2> depending on which one is online

---

### Post by killerdragon on 2007-11-25
Hmm intresting apporach.
Though, we probably don't want the script to sleep by itself, I will probably use cron to call the script. Ping -c1 -s1 (send 1 packet and send 1 databyte) would work a little bit better. Though ping -c2 -s1 would be more safe as I don't exactly have the best network in place :P
What I can do is make a file inside of the apache directory, call it FS, and it would contain which FS I would be using at that time. So if it detects that FS1 is up and FS1 is in the FS file, then do nothing, else change it to FS2 and change apache to use FS2.

I don't think the second option you provided would work, due to the nature of SMB and just general security concerns. I could be wrong though. I shall try it.

---

### Post by MJN on 2007-11-25
Your requirements sound extremely lopsided - do you really want to achieve what you've stated or is it just a bit of fun?

You say that you strive to achieve zero downtime yet also that your network is far from perfect. Is there really such benefit in having hot-swappable file with such flakiness? What exactly will it achieve?

I think you'd be better off with a single disc serving Apache and have a second as hot standby - either automatically with a RAID1 setup or manually syncd/swapped. This latter solution has numerous drawbacks including the delay of states between a new disk write and the associated mirroring taking place.

How often do you propose to upgrade the disks?

Mathew

---

### Post by killerdragon on 2007-11-25
I will upgrade whenever the disks start to get full, which would probably occur once a year.

I think you are taking it out of abstract thinking. This is only the idea gathering.
The way I would implment it wouldn't be doing everything in 5 min.
What I would do is take the first FS offline, upgrade the hard drive in FS1. Next day, replace the HD in FS2. Thus that leaves enough time for syncing to take place.

The proposed idea is not a bad idea at all. Sure there are probably better ways to accomplish this, but that is a decent idea.
And I don't think you read my second post, there is only IDE drives in there. There are myths saying that you can hotswap IDE drives, but its almost guarnteeded that it wont work (or would destory the drive). So RAID would be out of the question because in order to replace a HD I would have to shut the server down. I am trying to accomplish this without having to shut the server down and actually work on the hardware in the main server (as it is not only a pain, but goes against what I trying to do).

What do you think DFS in Windows Server 2003 does? It does similar to this but a little more complex. DFS will copy the same data to different DFS servers, and Windows Server 2003 will detect when one goes down and not send any data or users to that one. DFS also has an algorithm built in to decect heavy network load on one DFS server and 'knows' when to load balance to other DFS servers, but thats another bed time story...

Actually I have Windows Server 2003, which may work. But then I would have a single point of failure.

What am I trying to accomplish?
A non single point of failure, hot swappable disk system using only IDE technology.
Then this would also be expanded to other servers on other networks to allow load balancing without too many headaches.

---

### Post by MJN on 2007-11-25
I didn't mean to offend - just thought your requirements sounded completely out of balance given an acknowledged weak network connecting your resilient fileserver(s) with the web servers.

Given you've only got IDE drives (howcome? if this is a business-critical application, which it sounds like it is, then the expense of hot swappable drives is justifiable without second thought) then, as you say, you won't be able to swap out drives within a machine. However, you can do this on a logical level amongst the entire system i.e. taking one file server down to swap its disk whilst the other other is still up however your proposal to use rsync won't cut it because it doesn't operate in real time - any change to disk A will be delayed before being in use on disk B. The fundamental requirement of having two, or more, mirrored file servers is that each should have the same view at any instant of time (assuming they are both working) - if you don't achieve this then you haven't got resilience.

My suggestion is to look at what you are *really* trying to achieve, i.e. what risks you are trying to mitigate. Your requirements stated thus far are solutioneering i.e. you are stating *how* you want to achieve something and not *what*.

What risks do you face with regards to file/data availability? Disks failing? Servers failing? Network failing? What is an acceptable annual downtime (don't say zero - that's not achievable)?

For load balancing what is it you're trying to achieve? Is file system access *really* your bottleneck? Surely your line speed is less than the throughput of any one file server so adding another is not going to help.

This is all just food for thought, but I really do think you've got ahead of yourself towards a solution to a problem you've yet to define (rsyncing between drives shows you haven't assessed and defined this, not that you just haven't posted it). ;)

Mathew

P.S. Is there any reason you need to have the file servers seperate? How about USB drives on the web server? Far better performance than networked file server access, hot swappable, expandable... Of course there are many reason why these would not suffice but from the info we know so far its a fair suggestion.

---

### Post by koenn on 2007-11-25
While I found this an interesting problem (in terms of "how hard would it be to come up with a poor man"s implementation of a redundant file server ?") I do think MJN has some valid points, in that you should consider the what before the how (and the thing I offered is very much 'how').

For one, it is not necessarily a good idea to use a file share as document root for a web server, as it introduces additional points of failure (network hardware, network congestion, ...) and possibly performance loss. A sollution with redundant web servers in stead of redundant file serverds might be more appropriate. 

You seem to have written of RAID completely. I agree that you can't rely on hot-swapping of IDE drives, but the redundancy of a RAID system buys time : when a disk fails, the system remains operational so you have the tiime to get a second, identical  web server operational, then shut 1 down and bring the other one up. Total down time : 5 minutes ? And if they're truely identical (i.e. same hostname, same ip address, same data, ...) it's still almost completely transparant to the clients.

Again, as MJN says, you can only evaluate these sollutions ("how") if you're clear on *what* you're trying to achieve,

---

### Post by killerdragon on 2007-11-25
I was thinking about load balancing apache, but then I probably would have to redesign the whole system.

If I had the money to upgrade to SATA I would in a heart beat. Then RAID would be my main concern. But, when you are the only person working on a system like this, you are more concerned about the easiest/fastest/cheapest method to get a system up a running rather than efficiency. As of right now there is not that much data being transfered over the network, probably 1% capicity if that. As far as performance loss, 10/100 has been tried/tested/proven to be somewhat reliable, and you even have to factor in the actual output from the network to the internet, it almost will never be the full 100 (At least not where I live). Those are all good points, and if I had the time and the money to properly implent something, I would jump all over it.
I'm the type of person who puts the square peg in the round hole, instead of just going out and buying a round peg I buy a saw and I cut the sharp edges of the sqaure peg off to make it fit into the round hole :).

---

### Post by MJN on 2007-11-25
> **killerdragon said:**
> I'm the type of person who puts the square peg in the round hole, instead of just going out and buying a round peg I buy a saw and I cut the sharp edges of the sqaure peg off to make it fit into the round hole :).

I like it...

(I suppose there's some benefit in doing that as not only do you get your peg but the cutoff corners might come in userful too!) ;)

Mathew

---

### Post by koenn on 2007-11-25
> **killerdragon said:**
> I
I'm the type of person who puts the square peg in the round hole, instead of just going out and buying a round peg I buy a saw and I cut the sharp edges of the sqaure peg off to make it fit into the round hole :).
sounds like something I would do ...
and added benifit besides the cut-of corners : after a sufficient number of square pegs and round holes, you'll have learned a decent bit of carpentry / woodwork.

---

### Post by killerdragon on 2007-11-25
I would learn then I should have just gone out and bought a round peg. Though, I don't look at it like wasted time, I see it as a learning experience.
Knowledge is power! :-P

---

### Post by kretara on 2007-11-26
Have you looked at Heatbeat? ([http://www.linux-ha.org/](http://www.linux-ha.org/))

Sounds like this would work fine for you, although you would need another box (can be a cheap old box) to be the heartbeat server for your 2 file servers.

---

### Post by koenn on 2007-11-26
yep, looks interesting - it's pretty much what i meant with clustering a few posts back. I'd say it's worth a look, especially as they explicitely mention Ubuntu as one of their supported platforms.

---

