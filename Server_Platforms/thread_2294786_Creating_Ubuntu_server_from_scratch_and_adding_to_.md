---
title: "Creating Ubuntu server from scratch and adding to existing network"
date: 2015-09-13
forum: Server Platforms
---

### Post by Tom_Westwood on 2015-09-13
Hi All,

I'm completely new to Ubuntu with only experience with Windows machines in the past. I've never set up a server before, but from the information I've found online it seems as though Ubuntu might be the easiest way to go to create a new server for free (I may be wrong here!).

I'm looking to create a private server on a University network (I have their permission, but am currently just trying to create the server before attaching it to the network), that will only allow access to a small group of people who are working on the same project as myself (10 or so of us). We would like to be able to access this server remotely so that we are able to access the files whilst away from the University.

My knowledge is pretty basic when it comes to servers, and less when it comes to Ubuntu, but I shouldn't have any problems installing the OS onto the machine. The University will help me when it comes to attaching the server to their network.

Any information provided would be greatly appreciated, in layman's terms if that's at all possible!

Kind Regards,

Tom

---

### Post by Bucky Ball on 2015-09-13
*Thread moved to **Server Platforms**.*

Welcome. I know you're new here but you'll get more relevant help here. 

Have you researched [installing a Ubuntu Server]("https://duckduckgo.com/?q=install+ubuntu+server+14")? There already is a Ubuntu Server version. All you need to do is install it. As for setting it up so it will work ok with your uni network, that would depend a lot on your uni setup and only they can help with those details. Also on what you require from the server and how.

You're better off framing some more specific questions: get a test machine, make a start on it, install Ubuntu Server, and ask questions when you get stuck. Good luck. :)

PS: Stick with LTS releases for servers. They are supported for five years. The interims are for nine months and you don't want to be upgrading servers every six months. 14.04 LTS is the current LTS release.

---

### Post by Tom_Westwood on 2015-09-13
Hi Bucky Ball,

That's great thank you. I'll install that on the machine and see how far I get before getting stuck! I'll make sure to ask the questions in that forum in future.

Thanks!

Tom

---

### Post by SeijiSensei on 2015-09-13
Here are some important basic questions:

1) Will this machine have a public IP address on the Internet?  If so, who is responsible for reviewing the machine's security and keeping it up-to-date?

2) If the machine is on a private network behind the university's firewall, will they forward ports for you?  If not, how will you communicate with it from outside the university?  If the private network is visible to others on campus, the same security issues apply.  Consider all the machines that can see your server hostile and defend accordingly. 

I wouldn't run any more services besides openssh-server and have people use SSH clients to log in and SCP or SFTP to exchange files.  Give your users local logins on the box itself.  If they need to share files, put them all in a group and create a directory with group-writable permissions.

---

### Post by MAFoElffen on 2015-09-13
> **Tom_Westwood said:**
> I'm looking to create a private server on a University network (I have their permission, but am currently just trying to create the server before attaching it to the network), that will only allow access to a small group of people who are working on the same project as myself (10 or so of us). We would like to be able to access this server remotely so that we are able to access the files whilst away from the University.
Tom--

I recently just finished the same at my school, for a dB Server, for access from various CS courses.

I didn't see your locale, so will speak with a bit of generalities. Talk with the IT Infrastructure Sys Admin at your University... He's the one that will assign/give you your IP address for you server and have to open up ports for the services you will provide. He can help you make the connections from the outside world to your server. He can tell you of their policies and if it needs to be a part of a larger domain to make that connection. They may already have a Host for virtual server services, where you may not have to do a metal install. That would also free you up from having to do your own backups and summarized administration.

Ask him about what infrastructure them have in place presently. They may already have VPN services in place. That would be a way to provide secure services into your server, for access to your files. Access will probably be provided as members to a group. If VPN is in place in that infrastructure, then he can help you determine what you need on the server and clients ends to make that work. Some students and faculty have VPN access to their servers, through Cisco VPN, then a through a remote desktop...

Ask him about intermediate application server services. On our system, some users, according to their access privileges, have secured remote access to apps, which have access to their shared files... invisible (to the user) to what server they might actually be on.

For me, I lean to Ubuntu Server. It is my first choice, and is easy (for me) to plug into a bigger scheme or alone. But if you are part of a bigger picture, you need to be aware of what you need to do to be part of that "system." What your OS is is not as important, when you think of services you need to provide, and how they fit together in the bigger scheme. My niche is getting things to work together.

---

### Post by TheFu on 2015-09-13
+1 to ssh and sftp. These are provided by openssh-server.  If you force ssh-keys for authentication, it is secure from anywhere in the world.  Add on fail2ban to block brute force attacks and don't forget to enable a firewall - ubuntu comes with it, but doesn't setup any rules by default.

Sadly, much of what you've learned in Windows will not be helpful. IP networking, subnets, work that same, but all the commands are different.  Also, get used to managing settings by modifying text config files, then restarting the daemon to re-read those changes.  Learning linux is like learning a new language. It takes that level of effort, especially for server administration.  Embrace the shell/CLI interface.  Free PDF: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
Plus don't forget the manuals at help.ubuntu.com which explain the mechanics to get X, Y, Z working, but not usually the security implications.  

**Definitely learn directory and file permissions** - these are the cornerstone of all Unix security. It controls access to everything.  Follow a tutorial, create some different user-accounts, mix some groups in - some shared, some not, and spend 30 minutes trying all the different permission bits to see what each userid can and cannot access.  It is subtle and genius.  Most of Unix is.

---

