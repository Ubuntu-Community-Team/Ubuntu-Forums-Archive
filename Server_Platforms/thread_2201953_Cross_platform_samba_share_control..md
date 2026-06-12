---
title: "Cross platform samba share control."
date: 2014-01-26
forum: Server Platforms
---

### Post by Philip_James on 2014-01-26
Good evening all!

This is my first post here although I have viewed these forums a lot over the last few weeks.

Please bear with me, I am from a Microsoft background (please don't hate me) and until about a month ago had never touched Ubuntu at all. My business now has a requirement to use it, and I have been quite literally thrown in at the deep end and been tasked with its deployment into a virtualised environment..... I must admit, I didn't like the idea of implementing Ubuntu into a Windows network, however, after playing with and implementing Ubuntu server into our scenario, I'm kinda hooked! I am totally surprised how easily I have picked the OS up, and genuinely pleased how you all respond to others questions no matter how trivial or complex they are. 

I have a question regarding controlling shares created on Ubuntu from a Windows server for admins that will not have experience or knowledge of being able to do such changes within the Ubuntu server. Before I get to that question/scenario, here's a bit of background info on how I have currently got this system setup. I'm fortunate that it is not currently a live environment so have the ability to manipulate and rebuild the environment should I need to.

The environment currently consists of the following;
Physical HP Proliant DL 385g8, 32core AMD CPU, 64gb Physical Memory running MS Windows Server 2012 whos primary role is providing the MS Hyper-V service.
On this physical are the following virtual servers;
1 x Windows Server 2012 Primary Domain Controller - Active Directory, DNS, DHCP
1 x Windows Server 2008 acting as an application server
1 x Windows Server 2003 providing legacy application support
1 x Ubuntu Server 13.10 providing file and print services.

So far, so good. All servers are built and partly configured. All servers are joined to the domain and can communicate with one another no problem.

Concentrating on the Ubuntu server specifically, I have completed the following steps (after a pretty standard install of course);
1> Installed Desktop Environment (I have come from Windows, did you expect anything less) by running 'sudo apt-get install --no-install-recommends ubuntu-desktop' from the terminal
2> Synchronized Time with NTP Server by running** '**sudo apt-get install ntp' and edited the ntp servers to include the PDC.
3> Joined the server to the Windows domain by installing 'Likewise open' with the following command 'sudo apt-get install likewise-open likewise-open-gui' and then running 'sudo domainjoin-gui' to do the actual join to the domain. I have then updated the following file /etc/lightdm/lightdm.conf.d/10-ubuntu.conf to allow domain user logon (as follows);
[SeatDefaults]
user-session=Ubuntu
# to disable guest login
allow-guest=false
# to enable user login manually
greeter-show-manual-login=true

I can confirm at this point a domain user can successfully logon to the Ubuntu server and that a computer account has been created in AD.
4> Setup and configured Samba shares with instructions from [here]("http://wiki.samba.org/index.php/Setup_and_configure_file_shares").

At this point, everything is set. I can see the share from a Windows server no problem. My requirement from here is to manage the share permissions from the Windows PDC. Unless I have misread the link contained in point 4 above I should be able to do this, however when I follow the steps listed I can only specify users/groups from the Ubuntu server not from the Windows Active Directory domain.

I would be eternally grateful if someone could confirm firstly if I can manage an Ubuntu Samba share from Windows with AD users/groups, and if possible, what I may have missed along the way?

I apologies for the long winded thread, I'm sure I have missed something out, so please ask any questions if you require.

Many thanks for taking the time to read my post!

---

### Post by DuckHook on 2014-01-26
Hello Philip and welcome to Ubuntu, Linux and the forums,

Can't help with the technical stuff as I am not a server or AD expert. Just wanted to welcome you and note the following:

1. You are far from hated. In fact, we just love seeing MS visitors. We understand that you won't be dropping your MS needs in a corporate production environment, nor passing on the GUI, but the addition of Linux tools will help you get more out of your IT environment for sure.

2. You may wish to consider 12.04 for a stable VM server. 13.10 will reach end of life in June (non-LTS versions are supported for only 9 months) so for production purposes where you don't need the latest bells and whistles, you may be better off with a long-term stable release.

3. It's completely understandable how you would think that yours is an absolute beginners situation, but the level of your question is actually better suited for the Server Platforms or Virtualisation forum because that's where those respective gurus hang out. You may wish to have one of the moderators move it into one of those.

...and that's about where my expertise peters out. If a guru is lurking and can answer your question here and now, great. But if not, don't give up; have your thread moved to the proper forum instead.

---

### Post by Philip_James on 2014-01-27
Thanks for the welcome DuckHook!

A bit of an update for anyone that is interested.....

I can now manage the Ubuntu Samba share permissions from within windows. I had misconfigured the /etc/fstab file.

So although I can manage the share permissions, I'm unable to manage the folder security. Now I accept it is possible that I have just assumed that I would be able to manage the folder security and that in reality I cannot do so, maybe someone could confirm this either way?

If not possible I need to be able to secure the Samba shares with AD users/groups but am having real issues setting this up. Based on the fact I am a real newcomer, could anyone give me tips on how to secure files/folders on Ubuntu with AD users/groups?

Many thanks in advance

---

### Post by koenn on 2014-01-28
I think what you're trying to do is not impossible, but it's a bit tricky
also, I used to do thise using "winbind" - I'm not quite sure how this overlaps with likewiseOpen, but it'll give you an idea.

IIRC, what you need is

1/ a way to map AD accounts to samba accounts. You probably have that working as you can assign share permissions
2/ this should also work with filesystem permissions although you may have to explicitely map a  Domain Administrator account to the root account of the ubuntu server because root will have to set te file modes on the ubuntu server
3/ you may want to install posix acl on the ubuntu server because they behave more like the NTFS ACL your windows admins are used to.

The thing to keep in mind is that the windows dialogs you or your collegues are using to set permisions expect to be setting NTFS ACLs on direct attached storage in a windows server, but you're using some trickery to translate that to tweak samba security settings and set filesystem modes on an ext filesystem ... it will mostly work but it may sometimes be necessary to check and adjust an the ubuntu side directly. 

Here are some old notes:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
I don't recommend you follow them to the letter, just take them as context and for inspiration about what to look for in newer tutorials, as I expect that both Samba and Ubuntu have been improved for this sort of integration and there are newer and better ways to do this that what's in that writeup. (There's also some stuff you won't need, like tape backup and quota ; thte page is actually some personal notes from something i did to temporarily provide some extra disk space while waiting for a NAS to be ordered)

Good luck, and have fun.

---

### Post by bab1 on 2014-01-28
As @ koenn has said; take these links as inspiration rather than something to follow literally. 

 I believe you will need ACLs and the VFS module "acl xattr"  This saves NTFS-ACLs in Extended Attributes (EA) of the Linux file system 
[http://www.samba.org/samba/docs/man/manpages/vfs_acl_xattr.8.html]("http://www.samba.org/samba/docs/man/manpages/vfs_acl_xattr.8.html")
[http://agix.com.au/blog/?p=2124]("http://agix.com.au/blog/?p=2124")
[http://ubuntuforums.org/showthread.php?t=2200258]("http://ubuntuforums.org/showthread.php?t=2200258")

Google search on Samba4 and Windows Domain Users
[https://www.google.com/search?q=domain+users+access+to+Samba4+shares&btnG=Go!]("https://www.google.com/search?q=domain+users+access+to+Samba4+shares&btnG=Go!")

Be careful to look only at Samba4 information.  Most tutorials are on Samba3 which has no AD components.

---

### Post by koenn on 2014-01-28
> **bab1 said:**
> 
Be careful to look only at Samba4 information.  Most tutorials are on Samba3 which has no AD components.

That's not entirely correct. IIRC,  Samba4 was greatly improved wrt AD integration (up to being able to act as an AD DC) but Samba 3 was perfectly capable of being an AD Domain Member server, which is all the OP needs - he has DC on Windows machines and just needs a samba member server that honors domain authentication. 

That said, it is a good idea to use documentation that matches the version you're using, because in Samba, many features get added or modified/omproved  between (major) versions

---

### Post by bab1 on 2014-01-28
> **koenn said:**
> That's not entirely correct. IIRC,  Samba4 was greatly improved wrt AD integration (up to being able to act as an AD DC) but Samba 3 was perfectly capable of being an AD Domain Member server, which is all the OP needs - he has DC on Windows machines and just needs a samba member server that honors domain authentication. 

That said, it is a good idea to use documentation that matches the version you're using, because in Samba, many features get added or modified/omproved  between (major) versions

I was referring to the fact that the OP has **already installed Samba4 **.  Therefore the OP should only use Samba4 documentation.

---

