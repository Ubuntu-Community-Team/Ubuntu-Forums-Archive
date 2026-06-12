---
title: "How to ubuntu for a LARGE family?"
date: 2007-05-25
forum: The Cafe
---

### Post by muguwmp67 on 2007-05-25
I'm about to do some volunteer work for a large family in my area.  The [Nuzum family ]("http://www.foundationforlargefamilies.com/nuzum.html")in Ohio has been adopting special needs children for the past 20 years.  They currently have over 25 children, whom they home school.  They have been given a number of PC's.  The users of the PC's would be a wide range from Kindergarten through High school.

They were recently given 13 PCs by a local organization, but cannot use them.  They came with windows still installed, but each PC has a password attached to it.   I'm not sure whether it is possible to retrieve the passwords, but I consider this a non-issue.  The PC's were donated, and I believe the least I can do is maintain the donator's privacy by wiping the hard drives.

This means I'm left with a choice.  I can install 13 illegal copies of windows and Microsoft office, or beg for licenses from Microsoft.  or go with Ubuntu or another Linux variant. 

I've got some issues though, and wonder if you can help me come up with ideas.

Current thoughts:

[LIST=1]
[*]13 PC's for 25 children = either setting up a ton of user accounts, or setting up one account ('user'') and having the children share the /home directory of each computer.  Not a particularly elegant solution, but it would work.


[*]Use LDAP to authenticate user id's, but this still results on a separate home directory for each user on each pc they sign onto.


[*]Use edubuntu and thin-client instead of roaming, I'm currently concerned about this option as I do not know if their machines would have enough memory, and doubt that I have a PC with enough performance to serve 12 machines (I could look for a donation though).


[*]Use Windows and set up a roaming profile for each child
[/LIST]

I'm not sure if there are other options that I'm missing, is there something slick I could do with USB keys?  Can I use Samba to map their /home directories to the server?

Also, is there a simple way to configure one base desktop for all of the users.  I only want the administrator's account to see options that require root access?  I'm looking for some sort of way to set  up template /home directory for the users.

I'm not afraid to hit the pavement to find donators  for more hardware or software, but I have no idea of what I might need at this point.  I'm not a Linux guru, but I learn fast and am stubbornly persistent as long as I think  what I'm trying to do is possible.  Once an acceptable solution is implemented, I am going to try to get some press and publicity  for the organizations and products involved.

---

### Post by mips on 2007-05-25
Can you not put the home directories on a central server. I don't see why this cannot be done ?

---

### Post by muguwmp67 on 2007-05-25
Is that a function of LDAP?  Because it sounds exactly like what I'm trying to do?  I can do it if someone can tell me where I would configure this, so I can google for it.

---

### Post by GameManK on 2007-05-25
> **muguwmp67 said:**
> Is that a function of LDAP?  Because it sounds exactly like what I'm trying to do?  I can do it if someone can tell me where I would configure this, so I can google for it.

You would create empty home directories (mountpoints) on each computer and have all the home directories on an nfs server.  You can have the nfs mounted at boot either by putting the shares in /etc/fstab on each computer or by installing autofs and pointing the users' accounts to the right directories.  That's a vague summary, of course.

If you want to have each kid have their own account and home directory, set up one machine and then copy /etc/passwd to all the other ones to get the user accounts.

(Just set up something like this yesterday on an ubuntu machine :))

---

### Post by mips on 2007-05-25
Just google something like "Linux mount remote /home" or "NFS remote /home"

You would require NFS on the pcs though.

I have never done this but I'm almost 100% certain it can be achieved without much hassle.

Hopefully someone else here can give you more detailed instructions.

---

### Post by Babbage on 2007-05-25
I feel this is a prefect situation for Edubuntu: [http://www.edubuntu.com/](http://www.edubuntu.com/) It's very different network configuration to the usual home/office network as it involves a server and "thin client" configuration. It's a good choice if you've many older PC's because all you need is one well specified computer to act as server for the whole network. This server PC is the one you could be trying to get donated, (You could try Dell, considering they're so in love with Ubuntu at the moment!) In fact many standard desktop PC's can act as a server, but of course a fast processor, more memory, and bigger hard disk gives better performance.

I haven't used Edubuntu but I'd say, because it's server based, it would have built-in user accounts management (i.e all user accounts are probably stored on the server.) and setting these up should be a snap. More: [http://www.edubuntu.com/UsingEdubuntu](http://www.edubuntu.com/UsingEdubuntu) I don't think 13 computers between 25 children is necessarily a problem, because I don't think every child will need to be on a computer at one time.  A rota might be needed, (i.e half the children could use the computers in the morning, the other half in the afternoon) . Also very young children don't like to sit still for too long so they probably won't want to be at the computer for hours anyway.

Edubuntu FAQ's: [http://www.edubuntu.com/FAQ](http://www.edubuntu.com/FAQ)
Installation and Network Set Up: [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)
Screenshots: [http://www.edubuntu.com/Screenshots](http://www.edubuntu.com/Screenshots)

I'd strongly advise you against installing illegal software on any of your computers. The validation of software happens over the internet now, and with increasing frequency. So you risk the operating system, and office software being disabled at any time. It's just not worth it. Neither is using donated software, that sounds like a great idea, but then you have expensive and troublesome upgrades after a couple of years.

Your persistence and willingness to learn is very positive and will carry you through this project. Perhaps your local Linux User Group could help you out with the network setup and installation, if there's a college or university nearby approaching their computer studies department could prove useful. There's usually lots of Linux enthusiasts among the students who might be more than happy to help a good cause.

Good luck. :D

---

### Post by muguwmp67 on 2007-05-25
Don't worry, I don't consider pirated software a viable option here.  I also doubt any of these PC's would be able to run Vista.

The NFS remote  /home solution sounds like a definite winner.  I would really like to go the thin-client edubuntu route, but I do not know what kind of machines I have to work with yet.  If the machines have enough memory to thin-client, I'd really like to find a donated server to implement it.

Do you all think it is safe to install Ubuntu/Edubuntu in an environment where PC literacy is going to be a factor?  I'm think that with the kids, they are going to pick it up in no time.  I'm more concerned with system admin tasks.  This is definitely not an environment where anyone is going to feel comfortable with the CLI.

---

### Post by Babbage on 2007-05-25
I don't think computer literacy, or lack of same will be an issue. I use Ubuntu daily and I rarely need to use the terminal, but of course I could if necessary, so I can understand your concern. I think that once the network is properly configured there shouldn't be a lot of admin, it would help for them to have the phone number of someone locally who's familiar with the system and willing to help. I'm not familiar enough with Edubuntu to say much more. There's an Edubuntu community IRC channel and mailing list that may be able to help you further: [http://www.edubuntu.org/Community](http://www.edubuntu.org/Community)

---

### Post by %hMa@?b&lt;C on 2007-05-25
you can probably crack the SAM passwords on Windows if you are so inclined.  I would definitely  run Linux in this situation, however.  
[http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)
ophcrack may be able to get the passwords for you. 
Best of luck
Jeff

---

