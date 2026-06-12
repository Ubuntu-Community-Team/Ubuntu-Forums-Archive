---
title: "Can't find obvious answer...need some help"
date: 2006-07-04
forum: Server Platforms
---

### Post by evilscientist on 2006-07-04
I'm trying to set up ubuntu as a PDC server for my win xp laptop and desktop.  This so I can have a file and maybe printer server for my client machines....and for S*its and giggles.

From everything I've read, it looks like I've got everything set up right in Samba.

I've got my my smb.conf file all sorted out, no errors with testparm
I've added users with useradd and smbpasswd -a
I've added machines with useradd and smbpasswd -a -m

I can see the server in my network neighbourhood and access/browse folders on the samba server using a linux account login within the network neighbourhood.

However, when I try to go to My computer properties ---> computer name --->  Change.., and then put in my domain name and computer name and when prompted use root account and password (or any account and password) I get an Access Denied error.

Any suggestions as to what one little (but critical thing) I'm missing?

Everything I've read says this should work!

BAAAAHHHH!! :)

Evil.

---

### Post by datakid on 2006-07-15
I don't have the answer - but I'm glad I searched before I posted :) - this is _exactly_ the problem I am having too...

Any help would be appreciated. 

](*,)

I have a few other network oddities, but have largely followed the instructions exactly.

My dhcp is done by a third machine (debian, stable, firewall)

It's a fresh dapper install as of this morning, and I've been following the famous [http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4)

I'm using smbpasswd instead of tbdsam (could this be the issue?)

ok, i've set my log to level 10 in smb.conf on the server ("florentine"), and here's the result. What I did was I inserted a lot of ====================== these at the end of the /var/log/samba/smdb.log, saved it, then I tried to connect to the domain ("DAVEYST") on the workstation ("robin" or robin$) again. Then I got rid of everything before the ======================.

I'm not much of one for log files at this level - it reads terribly. But I presume someone out there can read it - you will notice on an initial peruse that it looks like it has successfully joined the domain, but maybe there is a timeout error? it's hard for me to tell - there is a lot of cruft at log level = 10.

anyway, I hope this content gets us closer to the solution.

---

### Post by evilscientist on 2006-07-15
I solved the problem.

Follow that protocol above almost to the letter.  I think the key thing was to install the quotas, which I hadn't done initially.  Also, make sure all your machine trust accounts are in place.  Hey, I almost sound like I know what I'm doing!!! :confused: 

I basically copied the smb.conf from that article and setup the quotas, except that I didn't use a static IP...and had an entry for the default ethernet connection...which is in the default smb.conf file...I just left it there.  The IP is assigned by the DHCP server on my router.  That worked.  And the lease time is 0...shouldn't be an issue.  

Also....do the psrt about setting up the root account instead of using sudo...it's easier and I think you need the root account active so that you can log into it the first time that you try to connect your workstation to the domain.  That's right, the first time you connect your workstation (win xp client) to the server, logon with the "root" account.  After that initial logon, you can logon with whatever account you've set up.

that smbuser step in that article is also good, makes the Administrator account on your desktop = root on the server, I also did that step with my other windows account.  Works fine.

Anyway....good luck....

---

### Post by datakid on 2006-07-18
Cheers for getting back to me evilscientist.

I've been mulling it over, adn I don't understand - I looked up quota on the web, and it doesn't seem like such a special program. 

I personally don't think that it makes sense that that would be the problem - as there is no requirement for quota to install Samba, and if there was (like samba was compiled with quota support for ubuntu), surely it would be solved in the "apt-get install samba" phase?

Also, I had a root account - I've been using Linux on and off for years, and while I like using sudo, I still want/need a root account?

I might try the samba mailing list - like I said, it looks like the connection is working....hmmm...

cheers
L.

---

### Post by evilscientist on 2006-07-18
Well...it may not have been the quota's, but it was definitely something I missed that is present in that tutorial...follow that, make your own mods to it and see what happens.

Evil.

---

### Post by datakid on 2006-07-21
ok, I've solved the problem from my end as well, at least I think so - I'm about to add all the other computers and hope that it flys, but I've joined my first computer to the DAVEYST domain.

The problem was definitely one of three things:

1. I hadn't uncommented the universe repositories in the /etc/apt/sources.list
fyi, I ignored the deb-src and only uncommented the deb - it's unlikely I'll want to get the source, and if I do, I know where to go.

2. I installed ssh and openssh-server - I hadn't done this part because I was ssh'ing into other machines willy nilly anyway and I made a stupid presumption.

3. the "invalid users = root" I had in my smb.conf :oops: 
lolz, bet it was 3. I have commented it out, and when I've added all machines, I will uncomment it.

anyway, back to work

Word of warning to ppl reading this thread:
ssh server needs to be installed.
also, I noticed that /etc/samba existed when I finished the initial install, but samba wasn't actually installed - I needed to apt-get it , if I remember correctly?

anyway, problem solved, cheers

---

