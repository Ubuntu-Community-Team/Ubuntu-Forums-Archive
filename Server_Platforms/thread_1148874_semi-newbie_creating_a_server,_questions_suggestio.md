---
title: "semi-newbie creating a server, questions? suggestions welcome"
date: 2009-05-04
forum: Server Platforms
---

### Post by Pnuts on 2009-05-04
Couple of questions before I get to far into this. I'm fairly new to Linux in general I want to setup a Web Server. This is not only for a learning experiance but to also host a public website for friends and family.

1. Other then setting up a web server, what are some great things you would suggest to have running on it? I am thinking mail and maybe a local time server for the house. Any other useful things out there? I have a Linux MCE system so I have no need for mythtv on this machine.

2. I want to get the most out of this learning experiance so I do not plan on selecting any additional packages during the install and going at it from there. Would anyone advise against this? Keep in mind im not a complete newbie and can get around with the command line ok, also, this would help me learn more as I go.

3. Partitions, I have 3x 320gb drives in the system and I plan to use software raid 5. Up until now I have used a single large partition for everything on Linux, but I would like to do it right on this server. I have a NAS, so user files will be kept to a minimum if at all on this server. Here is my proposed plan:

**/boot** - 500mb (as raid 1, I read software r5 doesnt work to good here) 
**/ (root)** - 5gb (software raid 5)
**Swap **- The system has 8gb of RAM in it, overkill, I know. Does the 2.5x RAM rule remain here? to keep all 3 drives usage similar when partitioning for raid, should i split the swap file over multiple drives, put it on a raid(lol)?
**/home** - 15gb (software raid 5)
**/tmp** - 1gb (software raid 5)
**/usr** - 15gb (software raid 5)
**/var** - everything thats left (software raid 5)

Am I missing anything, should I do it differently? If I take any of the suggested for question 1, should I change anything based on that? Maybe if I start using some VM software?

4. I was planning on using 9.04 server, would anyone highly suggest the LTS over this one? I kind of like the idea of doing another installation at 9.10 or maybe 10.04 to continue the learning process, so the length of support on it does not really concern me to much.

5. Anything that you might suggest I do, read up on, etc before i get started?

Thanks,
Pnuts

---

### Post by Iowan on 2009-05-04
SSH server is handy - essentially lets you run the server headless. My server acts as DHCP server, too.  I haven't managed to get LDAP server going, yet.  
Although a LAMP server is available at setup, there are some other guides, too. [ howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") usually has a "Perfect Server" article for current Ubuntu version.

---

### Post by gombadi on 2009-05-04
So you want a public facing web server that you want to use for web sites and as a learning experience - excellent idea, have a few of them myself :-)

You mention using VM software - That would get my vote.

Build the system as you want it for your home needs and then install,configure the VM software, install a virtual instance and use that as the public facing web site. That will make it easy to to take snapshots of the web VM and/or have a few different configurations that you can point your router to. 

As for what VM software to use - well there are many choices.
- I have used VMware server 1.x in the past - it works as long as you don't have more than a few on a host.
- xen is another option and it works very well. Would get my vote for your needs only because I have more experience with xen than kvm.
- kvm is the new talking point (RHEL have made it the default VM for new releases) - Have not played with it much but from what I understand it works very well.
- OpenVZ is what I currently use - may not be the best fit for your requirements.

As for partition sizes - I come from the use less partitions camp. The best partition layout will depend on what VM system you use - make the yes/no VM decision first.

If you are using the system as a learning experience then stick with the latest version - 9.04 - knowing you will have to spent a bit of time rebuilding it each release. I use LTS on my servers - I have rebuilt them enough :-)

---

### Post by Pnuts on 2009-05-05
Thanks for the info guys.

Looks like ill start with Openssh and get a rsa key going.

Decided on going with kvm. Ill leave the partitions I defined above and if I find something that would have worked better, ill run with that when ever I do a reinstall of the system.

I guess a VM for a web server and go from there. I'll just keep my eyes open for other fun things to do with a home server.

---

