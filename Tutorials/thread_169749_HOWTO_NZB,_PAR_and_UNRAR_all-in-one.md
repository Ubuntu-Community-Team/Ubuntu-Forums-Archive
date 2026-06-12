---
title: "HOWTO: NZB, PAR and UNRAR all-in-one"
date: 2006-05-03
forum: Tutorials
---

### Post by danalog on 2006-05-03
> New: [a version of this howto for OSX]("http://www.macbookfan.eu/2006/07/11/howto-nzb-par-and-unrar-all-in-one-for-osx/")

This is my first howto, and it is a small one :) 

I was looking for a way to process downloaded NZB files the most easiest way possible. That means downloading the NZB files to one directory, and let some program automatically download the binary posting, decode the files, check them with par2, repair if needed and then unrar the files and place the processed file in another directory.

What needs to be done:
[LIST=1]
[*]**Open a terminal**
[*]**Install needed files:** ```
sudo apt-get install python-dev python-twisted unrar par2
```
[*]**Download hellanzb to your userdir:**
[http://www.hellanzb.com/distfiles/hellanzb-0.9.tar.gz]("http://www.hellanzb.com/distfiles/hellanzb-0.9.tar.gz")

[*]**Unpack:** ```
sudo tar -xzvf hellanzb-0.9.tar.gz
```
[*]**Cd to directory:** ```
cd hellanzb-0.9
```
[*]**Run install script:** ```
python setup.py install
```
[*]**Copy config file:** ```
sudo cp /usr/etc/hellanzb.conf.sample /usr/etc/hellanzb.conf
```
[*]**Configure settings:** ```
sudo gedit /usr/etc/hellanzb.conf.sample
```
Look for: defineServer and change the account settings to your usenet account settings.
Change the PREFIX dir to: ```
/home/your-user-name
```
You can change the other directories to your preference but it is not needed. There are also a lot of other options in the config file, change if needed.

[*]**Run the program:** ```
hellanzb.py
```
[*]**Download a NZB file** and place it in: ```
/home/your-user-dir/nzb/daemon.queue/
``` or whatever directory you choose in the config file.
[*]**Finished files will be in:** ```
/home/your-user-dir/usenet/
``` or whatever directory you choose in the config file.
[/LIST]

Par2 files will only be downloaded from the server if needed for repair. This will save bandwidth :)

Happy NZB hunting :)

---

### Post by libbylib on 2006-05-07
sudo apt-get python-dev python-twisted unrar par2

should be

sudo apt-get install python-dev python-twisted unrar par2

---

### Post by rotten777 on 2006-05-13
[QUOTE=danalog]Happy NZB hunting :)[/QUOTE]




Awesome. A HUGE reason I couldn't just drop the Win32 platform has now been fixed. Thanks m8 :)

---

### Post by stivakos on 2006-05-20
Thanx. It is so useful I couldn't imagine. But I have two questions
1. If I stop the execution of the file, do I have to reload the nzb. from the start?
2. Can I edit the configuration file while it is running?

---

### Post by danalog on 2006-05-20
[QUOTE=libbylib]sudo apt-get python-dev python-twisted unrar par2

should be

sudo apt-get install python-dev python-twisted unrar par2[/QUOTE]
fixed

---

### Post by danalog on 2006-05-20
[QUOTE=stivakos]Thanx. It is so useful I couldn't imagine. But I have two questions
1. If I stop the execution of the file, do I have to reload the nzb. from the start?
2. Can I edit the configuration file while it is running?[/QUOTE]
1. Nzb's automatically resume when script is restarted.
2. I think you can edit but you probably should restart script to reload configuration. Share your results plz.

---

### Post by danalog on 2006-05-20
[QUOTE=rotten777]Awesome. A HUGE reason I couldn't just drop the Win32 platform has now been fixed. Thanks m8 :)[/QUOTE]
No prob just wanted my rig do the work for me, thought I'd share it with you all :)

offtopic: But I am a syshopper.... I tend hop from xp to linux to osx and back. At the moment I am trying to sell my system to get the funds for a new macbook with core duo so I can run osx the right way and run ubuntu and XP in Parallels. This way I get the best of three worlds in one kickass notebook. Especcially when Xen is ready begin 2007. Pure virtualisation... running xp/osx/ubuntu next to eachother at the same time!!! Awesome!!!

---

### Post by stivakos on 2006-05-20
[QUOTE=danalog]2. I think you can edit but you probably should restart script to reload configuration. Share your results plz.[/QUOTE]

Yes, I have to restart script to reload configuration. Thanx again.

---

### Post by dmorel on 2006-06-03
very excellent and simple method, much appreciated tutorial.

(in step 5, remove the cd .tar.gz from the directory you are changing to)

---

### Post by FerGeCo on 2006-06-05
I love hellanzb .. saves me alot of time to with parring and unrarring .. it's doing it all while i'm sleeping :D

Thanxz alot for the tutorial and for getting me to know about hellanzb (:

---

### Post by pubwho on 2006-06-05
Thatnks, this is brilliant.

However, does anyone know how I can set it up so that hellanzb.py loads up automatically at start up without a terminal window?

---

### Post by bugsbunny2002 on 2006-06-07
I created a little script that I put in /etc/init.d/hellanzb that uses the amazing screen.

```
#! /bin/bash
#
# hellanzb       Start the hellanzb.
#


NAME=hellanzb

trap "" 1
export LANG=C

case "$1" in
  start)
    echo -ne "Starting $NAME"
    /usr/bin/screen -S $NAME -d -m /usr/bin/python /usr/bin/hellanzb.py > /dev/null 2> /dev/null
    echo "."
    ;;

  stop)
    killall hellanzb.py
    echo "."
    ;;

  reload)
    echo "."
    ;;

  reload-modules)
    echo "."
    ;;

  restart)
#    $0 reload-modules
    $0 stop
    $0 start
    ;;

  force-reload)
    $0 reload-modules
    ;;

  *)
    echo "Usage: /etc/init.d/$NAME start|stop|reload|reload-modules|force-reload|restart}"
    exit 1
    ;;
esac

exit 0

```

Then start it in runlevel 2-5.
```

ln -s /etc/init.d/hellanzb /etc/rc2.d/S20hellanzb
ln -s /etc/init.d/hellanzb /etc/rc3.d/S20hellanzb
ln -s /etc/init.d/hellanzb /etc/rc4.d/S20hellanzb
ln -s /etc/init.d/hellanzb /etc/rc5.d/S20hellanzb

```
So after Ubuntu start, go to this screen with
```
screen -R hellanzb
```
leave it with
```
ctrl-a d
```

---

### Post by pubwho on 2006-06-08
I type:

screen -R hellanzb

but all I get is a command prompt. Is it supposed to show the current progress when I do this?

---

### Post by rbgCODE on 2006-06-08
This is just awesome!!  Thanks man

---

### Post by medw1974 on 2006-06-08
It's probably pretty obvious to most, but I got caught out blindly copying and pasting ](*,) lol

Step 8 should be:

```
sudo gedit /usr/etc/hellanzb.conf
```

not

```
sudo gedit /usr/etc/hellanzb.conf.sample
```

Anyway thanks for a great howto, just what I was looking for.

---

### Post by rbgCODE on 2006-06-09
n/m I found someone local to come over.

---

### Post by JediPottsy on 2006-06-09
thanks

---

### Post by binks on 2006-06-09
code 8  part 2  should read 

Code:

/home/your-user-name/


not 


Code:

/home/your-user-name

this is v good im well impressed

---

### Post by TomH on 2006-06-09
python setup.py install

just though id add that runnin the above command gave errors, so i had to run it as:

sudo python setup.py install

:cool:

---

### Post by TomH on 2006-06-09
Also that screen doesnt work for me ? Just says new screen then ends? Back to the screen prompt

---

### Post by E-Jey on 2006-06-12
You have to install screen with "apt-get install screen" and don't forget to make it a executable with "chmod +x /etc/init.d/hellanzb"

---

### Post by TomH on 2006-06-12
[QUOTE=E-Jey]You have to install screen with "apt-get install screen" and don't forget to make it a executable with "chmod +x /etc/init.d/hellanzb"[/QUOTE]

Yeah its definatly installed, and it is a executable, when i try to run it the windows says New Screen... then after 10 seconds just returns to the prompt. I have followed you guide step by step twice now :confused:

---

### Post by kditty on 2006-06-12
when i try to run that first sudo command i get:

python-dev is already the newest version.
python-twisted is already the newest version.
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

---

### Post by kditty on 2006-06-12
ok i got it to work so far. thanks so much for this howto, usenet downloading html, graphics etc is the main reason i use windows still... plus the comfort zone of knowing whats going on, but this is definatly going to cause me to spend more time in linux. also its insane how much time this will save me if everything works out well.

im on dapper so im not sure if everything installed right but im praying it will. 20 minutes ago i was trying to find a program to do each of these things and you sum it up in one post. thanks a ton.

---

### Post by E-Jey on 2006-06-13
[QUOTE=kditty]when i try to run that first sudo command i get:

python-dev is already the newest version.
python-twisted is already the newest version.
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate[/QUOTE]

You have to enable the multiverse repository.

---

### Post by danalog on 2006-06-15
Hi everyone, thanks for the positive replies! It seems I made a few typo's and small errors in the howto. I will try to fix them soon.

At the moment I am trying to make Hellanzb work on my macbook (osx/intel), which is a little different and less documented. So, when I'm done with that, I'll post another [howto for OSX]("http://www.macbookfan.eu/2006/07/11/howto-nzb-par-and-unrar-all-in-one-for-osx/"). Maybe on another forum or on one of my own websites, don't know yet. There will be a link from this howto for all of you multi-os'ing peeps ;)

Have fun with your favorite nzb's :)

edit: [here is the nzb, par and unrar all-in-one howto for osx]("http://www.macbookfan.eu/2006/07/11/howto-nzb-par-and-unrar-all-in-one-for-osx/")

---

### Post by hannesz112 on 2006-06-15
Hi

I've got the progam installed only if i try to start hellanzb with the following code:

```
hellanzb.py
```
Then i get the following error message
```
Exiting: FatalError: Cannot continue program, required executable 'rar' or 'unra r' not in path
```

I don't know what to help !! :-P 

thnx

---

### Post by NobodySpecial on 2006-06-15
hannesz112 -

In terminal:
```
sudo apt-get install rar
```
This works in Dapper.

---

### Post by hype on 2006-06-17
Exellent script, just what a lazy guy like me needs :p

Btw i had to change setting in hellanzb.conf rather than hellannzb.conf.custom

---

### Post by hype on 2006-06-17
wow, there are even some colored feedback mesasges going on in console !
Just works perfectly fine m8!! Love that script :p

---

### Post by kditty on 2006-06-19
everything is working fine, but sometimes i get ahold of nzb files that have messed up data, and some of the rar files will be missing so the par2 verify fails. how do i run a par2 file to check the parity data myself after downloading the missing rars?

---

### Post by danalog on 2006-06-19
[QUOTE=kditty]everything is working fine, but sometimes i get ahold of nzb files that have messed up data, and some of the rar files will be missing so the par2 verify fails. how do i run a par2 file to check the parity data myself after downloading the missing rars?[/QUOTE]
This is a downside of Usenet. Some postings just aren't complete. Thats why there is parity, but if there is too much missing rar files then it cannot be helped.

If you have found the missing rars, place them in the hellanzb download dir and then place the nzb again, it will find the rar files and continu.

---

### Post by rbgCODE on 2006-06-19
[QUOTE=kditty]everything is working fine, but sometimes i get ahold of nzb files that have messed up data, and some of the rar files will be missing so the par2 verify fails. how do i run a par2 file to check the parity data myself after downloading the missing rars?[/QUOTE]

par2 --help would be a good place to start but basically -

par2 v parfile.par2 to check it
par2 r parfile.par2 to repair it

---

### Post by kditty on 2006-06-19
[QUOTE=rbgCODE]par2 --help would be a good place to start but basically -

par2 v parfile.par2 to check it
par2 r parfile.par2 to repair it[/QUOTE]

ok that worked fine, once i figured out that its case sensitive lol. this whole time i was trying to check that parity and it wasnt working i thought something was messed up. i still have to get used to all this case sensitive stuff ;x thanks for the help guys.

---

### Post by Lil_Eagle on 2006-06-21
This works great, but I have one stupid question.  When hellanzb finishes downloading everything, it moves the files to the appropriate directory as specified in the conf file, but the owner of everything it downloads is root, which means I can't rename them (or move them) unless I open a shell.

Is there a way to tell hellanzb which permissions and owner to set on the files that it finishes with.

I assume it is setting the owner as root because it is a daemon, and it loading automatically at startup.  Should load it another way?

---

### Post by rbgCODE on 2006-06-21
[QUOTE=Lil_Eagle]This works great, but I have one stupid question.  When hellanzb finishes downloading everything, it moves the files to the appropriate directory as specified in the conf file, but the owner of everything it downloads is root, which means I can't rename them (or move them) unless I open a shell.

Is there a way to tell hellanzb which permissions and owner to set on the files that it finishes with.

I assume it is setting the owner as root because it is a daemon, and it loading automatically at startup.  Should load it another way?[/QUOTE]

dont start hellanzb.py with sudo and it will save everything under the users rights, and then you can do anything.

---

### Post by general alcazar on 2006-06-22
First, i would like to apologize for my poor english :-\" 

I wish to use 2 differents servers but I do not manage to modify correctly /usr/etc/hellanzb.conf

Have you a sample ??

Thank you

---

### Post by wousser on 2006-06-27
[QUOTE=general alcazar]First, i would like to apologize for my poor english :-\" 

I wish to use 2 differents servers but I do not manage to modify correctly /usr/etc/hellanzb.conf

Have you a sample ??

Thank you[/QUOTE]
```
# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'eweka',
             hosts = [ 'newsreader.eweka.nl:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'user',
             password = 'pass',
             #username = None,           # no auth
             #password = None,

             connections = 1,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )
defineServer(id = 'xs4all',
             hosts = [ 'newszilla.xs4all.nl:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = None,
             password = None,
             #username = None,           # no auth
             #password = None,

             connections = 3,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

# Uncomment this line to limit all server connections to the specified KB/s
```

---

### Post by Jon Snow on 2006-06-28
Thanks alot for the Howto ...work first time for me ( luck )...what a great app :)

---

### Post by jasonparekh on 2006-06-28
Wow, this program rocks!

Anyway, I've made a package for it.

It places files in:
- Source: /usr/share/hellanzb/
- Downloads/NZBs: /var/hellanzb/
- Config: /etc/hellanzb/
- Logs: /var/log/hellanzb/
- Initscript: /etc/init.d/hellanzb
- Binary symlink: /usr/bin/hellanzb.py
- Random docs: /usr/share/doc/hellanzb

It has an init script (based on the previously posted init script that uses screen) that will be launched on boot.

Unzip, sudo dpkg -i hella*deb, and place NZBs in /var/hellanzb/nzb/daemon.queue.  Only downfall is that it runs as root.

This is my first package, so let me know if I did something incorrectly..

Enjoy!
Jason

---

### Post by Lil_Eagle on 2006-06-29
Using that .deb seems a bit foolish to me.  Why should it be running as root?  That's the same problem that I was running into before.  My regular account can't move the files from the download directory.  I have to open a console (or run konqueror as root) to do it.  

Why not just have it run after logging in?  That way it can use the user id to create the files.  It seems to me that there are enough deamons being started in  init.d, why add another one?

I will say, you're on the right track though.  It doesn make it a lot easier for people, but they still need to configure it with their server information.

Also note, that by creating a .deb for it, you're locking it to that specific architecture, which means for people running AMD64, or PPC, they have to install it with: ```
sudo -dpkg -i --force-architecure hella*.deb

```
Since it is only a script, it isn't dependant on the architecture of the OS, but dpkg doesn't know that.  That's why the multi-arch distro needs to be built.

---

### Post by jasonparekh on 2006-06-29
[QUOTE=Lil_Eagle]Using that .deb seems a bit foolish to me.[/QUOTE]
I'm not sure I would consider it foolish.  It's much cleaner than using the setup script provided (files get thrown anywhere, it will be difficult to remove them, and also dependencies are taken care of--these are major benefits of package management).

[QUOTE=Lil_Eagle]Why should it be running as root?  That's the same problem that I was running into before.  My regular account can't move the files from the download directory.  I have to open a console (or run konqueror as root) to do it.[/QUOTE]
I agree, it shouldn't be running as root.  I think the proper thing to do is create a hellanzb user, chmod g+w the directories, and add your regular account into its group.  I'll add this in later.  I use the console more than konqueror (so sudo isn't an issue), so I didn't realize running as root would be that troublesome.

[QUOTE=Lil_Eagle]Why not just have it run after logging in?  That way it can use the user id to create the files.  It seems to me that there are enough deamons being started in  init.d, why add another one?[/QUOTE]
Heh, I disagree with this completely.  This program is meant to be a daemon, and hence its startup should be in init.d.  Just because yuo have a thousand and one daemons runing already doesn't mean you should refrain from putting things that belong there elsewhere.  Again, about 'the user id to create files', once I do the hellanzb group, you'll be fine.

[QUOTE=Lil_Eagle]I will say, you're on the right track though.  It doesn make it a lot easier for people, but they still need to configure it with their server information.[/QUOTE]
Yeah, I completely forgot about the server info :)  I guess this would be a good time for me to learn how to do configuration dialogs for packages.

[QUOTE=Lil_Eagle]Also note, that by creating a .deb for it, you're locking it to that specific architecture, which means for people running AMD64, or PPC, they have to install it with: ```
sudo -dpkg -i --force-architecure hella*.deb
```
Since it is only a script, it isn't dependant on the architecture of the OS, but dpkg doesn't know that.  That's why the multi-arch distro needs to be built.[/QUOTE]
Interesting.  Okay, so as long as I add that it's suitable for more architectures to the package control scripts, it should be okay right?


Thanks for the comments, I'll hopefully release another version soon..
Jason

---

### Post by Lil_Eagle on 2006-06-29
> I'm not sure I would consider it foolish. It's much cleaner than using the setup script provided (files get thrown anywhere, it will be difficult to remove them, and also dependencies are taken care of--these are major benefits of package management).


Foolish was far too strong of an adjective.  Perhaps unwise would have been better.  I agree with the idea of a package.  Personally I would prefer a better interface than the console (or screen).  Similar to SABnzbd, which BTW is also written in python.  I hadn't heard of it until yesterday thanks to a local magazine.  You can find out more about it from [http://sourceforge.net/projects/sabnzbd]("http://sourceforge.net/projects/sabnzbd")

I will have to try it.

More on topic, I like the idea of having hellanzb running as its own user.  Your idea would solve the root ownership issue versus my starting it when kde stars.  I still dislike the idea of a daemon running when it isn't being used.  Then again, its not like it takes up that much space or slows things down.  I am still used to the Windoze world of having 4 copies of svchost runing and each taking up 30 megs (and not knowing what any of them are doing :confused: )

I don't know if a configuration dialog is what you want to do.  Some apt front ends don't display them properly.  I think it's good enough to say in the docs that the user needs to edit the .conf file.  Wine for example requires that you rune winecfg.

As for the archeticture problem, a lot of people forget about us 64-bit users.  That's part of the problem running a 64-bit version of K/ubuntu.  But, it causes me to learn more, which is only a good thing.  I managed to install your .deb, then remove it (had to manually delete directories, dpkg -r did not do it).  I have it installed and running using my home dir as the howto suggests.

<rant>
One thing I can say now that I am using this, I am finding that I don't need to dual boot.  Between pan, binsearch.info, most all of my needs are met.  I will keep the partition for the few times I feel like gaming.  Which isn't often lately because this computer is quite frequently busy downloading. :)
</rant>

---

### Post by allnameswereout on 2006-06-29
[QUOTE=jasonparekh]Wow, this program rocks!

Anyway, I've made a package for it.

It places files in:
- Source: /usr/share/hellanzb/
- Downloads/NZBs: /var/hellanzb/
- Config: /etc/hellanzb/
- Logs: /var/log/hellanzb/
- Initscript: /etc/init.d/hellanzb
- Binary symlink: /usr/bin/hellanzb.py
- Random docs: /usr/share/doc/hellanzb

It has an init script (based on the previously posted init script that uses screen) that will be launched on boot.

Unzip, sudo dpkg -i hella*deb, and place NZBs in /var/hellanzb/nzb/daemon.queue.  Only downfall is that it runs as root.

This is my first package, so let me know if I did something incorrectly..

Enjoy!
Jason[/QUOTE]

Can you post your debian/ dir or the dsc, diff and orig src? I'd like to make some modifications and make a package for a different architecture.

---

### Post by Zorro on 2006-06-30
Quick question, I noticed in the .conf an option for a newzbin account... what implementation are you planing on putting in.. Or does it do, that I can't see?

Thanks...

z.

---

### Post by czz7661 on 2006-07-03
There are some good front ends for this program that allow you to just upload the newzbin nzb id.  To get it to work you have to add it to the conf file.  But the one I got working that I like best is call hellahella, really nice interface.  Much prettier than sabnzbd.

---

### Post by brownjl on 2006-07-05
Hello all,

Just like to say thanks for this how to, I am a new linux user and not being able to process nzb files in a sensible way has stopped me switch to linux in the past.

Anyway, I need some help, I have created a user and group called nzb-user and created a copy of the init.d script posted ealier, how do I run that script /etc/init.d/nzb as the user nzb-user? A friend told me to change the ownership of the file to nzb-user which I tried, and change the special file settings but this hasn't worked..

Any ideas?

Cheers

James

---

### Post by darkblade on 2006-07-05
I'm having the same issue and I've checked to make sure everything is running as it should be.

---

### Post by allnameswereout on 2006-07-06
[QUOTE=brownjl]Hello all,

Just like to say thanks for this how to, I am a new linux user and not being able to process nzb files in a sensible way has stopped me switch to linux in the past.

Anyway, I need some help, I have created a user and group called nzb-user and created a copy of the init.d script posted ealier, how do I run that script /etc/init.d/nzb as the user nzb-user? A friend told me to change the ownership of the file to nzb-user which I tried, and change the special file settings but this hasn't worked..

Any ideas?

Cheers

James[/QUOTE]

Hi James (and darkblade),

User ownership would only work it if it were setuid and group ownership would only only work if it were setgid. However both of these methods are depricated.

You don't run the script as user. You run the script as root and in the script you switch to a user account (e.g. *su - nzb-user*) then executing the command *or* you run a command as user (e.g. *su -c 'whoami' nzb-user*).

Some init-scripts, especially nice (debianized) ones, allow one to set this kind of stuff up in /etc/default or in the configuration file of the daemon (e.g. Apache, PowerDNS, Pure-FTPd, and so on). Other init-scripts have to be modified themselves but this is considered ancient and ugly. In the case of this software YMMV. I'm not able to tell as i have not studied the software.

---

### Post by danalog on 2006-07-11
Hi all, I've made a new version of this howto for OSX if anyone is interested:

[Howto  nzb par and unrar all in-one for OSX]("http://www.macbookfan.eu/2006/07/11/howto-nzb-par-and-unrar-all-in-one-for-osx/")

---

### Post by gurgle on 2006-07-12
trying to run hellanzb:

Downloading [http://hellanzb.com/hellanzb/hellahella/trunk#egg=hellahella-dev](http://hellanzb.com/hellanzb/hellahella/trunk#egg=hellahella-dev)
Doing subversion checkout from [http://hellanzb.com/hellanzb/hellahella/trunk](http://hellanzb.com/hellanzb/hellahella/trunk) to /tmp/easy_install-WcDJ2h/trunk
sh: svn: command not found
Processing trunk
error: Couldn't find a setup script in /tmp/easy_install-WcDJ2h/trunk

---

### Post by gurgle on 2006-07-13
new version of sabnzbd is out: 

[http://sourceforge.net/projects/sabnzbd/](http://sourceforge.net/projects/sabnzbd/)

I am having problems installing it thought. when i run

"python setup.py install" it doesnt install :???:

---

### Post by allnameswereout on 2006-07-16
> **gurgle said:**
> trying to run hellanzb:

Downloading [http://hellanzb.com/hellanzb/hellahella/trunk#egg=hellahella-dev](http://hellanzb.com/hellanzb/hellahella/trunk#egg=hellahella-dev)
Doing subversion checkout from [http://hellanzb.com/hellanzb/hellahella/trunk](http://hellanzb.com/hellanzb/hellahella/trunk) to /tmp/easy_install-WcDJ2h/trunk
sh: svn: command not found
Processing trunk
error: Couldn't find a setup script in /tmp/easy_install-WcDJ2h/trunk

sudo apt-get install subversion

---

### Post by jms830 on 2006-07-19
I put 2 nzb files in the queue folder and recieved this output, but nothing seems to be happening. I don't really know what to do.

```
hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(giganews) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: sps06
Found new nzb: sps07
```

---

### Post by TuxCrafter on 2006-07-20
Hello,

How do I get par2 to remember witch files are already scanned and are not changed so that it can contrinue its scan.

---

### Post by rbgCODE on 2006-07-31
> **jms830 said:**
> I put 2 nzb files in the queue folder and recieved this output, but nothing seems to be happening. I don't really know what to do.

```
hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(giganews) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: sps06
Found new nzb: sps07
```

Sounds like you have incorrect server settings.  You can puyt it into debug mode if you want to make sure.

---

### Post by zenwhen on 2006-08-01
This guide REALLY helped me out. Thanks!

---

### Post by rlynch on 2006-08-01
Yea I gotta say. . .Pan. . .sucks. I don't mind using a 'text' reader, as long as I have nzb support. Thanks for the tut.

---

### Post by rlynch on 2006-08-02
I see the folders that are being made have ownership permission by root. . .but im not root, im 'example'. so it doesn't let me delete the files or folders after i've watched what i downloaded(talking about files in my usenet folder)

---

### Post by rlynch on 2006-08-02
nvm, i see sudo chmod 777 blah works, then I can delete it in the folder. still seems dumb to do it like that though.

---

### Post by TwoWordz on 2006-08-09
Great post. I didn't know about hellanzb. 

Looks like there is a firefox extension to take care of the nzb files:

[http://z0g.org/hellafox/](http://z0g.org/hellafox/)

I just found out about it, I was on hellanzb's site trying to make hellanzb work on cygwin. I'm on my windows laptop so I didn't test it yet.

Sweeeeeeet.

TW

---

### Post by TNBY963 on 2006-08-10
Thanks a lot man! You freed up a lot of my time. I never got HJsplit to work smooth, but hellanzb does this in seconds. Really, I'm amazed.

And btw, I don't regret switching to ubuntu from XP. This community alone is reason enough!

---

### Post by fuzzmo on 2006-08-12
I got to say a huge thanks for the instructions - this is a brilliant program and with hellafox it has made the whole process just 1 step compared to 4-5 under xp.  A brilliant guide - mnay thanks dude!  Just need WoW to run under Wine/Cedega and then it truly is goodbye XP!!!

Thanks once again dude!

---

### Post by uncreative on 2006-08-13
I'm not sure if this has ever been mention before but I used [http://www.bnr2.org/](http://www.bnr2.org/) for my NZB files.  

Also, quickpar, and winrar work flawlessly under WINE.

---

### Post by gurgle on 2006-08-17
I would love a guide for installing Sabnzbd. the program itself is easy, its just the dependencies that are a biatch.

---

### Post by Ambimom on 2006-08-18
Hope someone is still reading this thread....I followed the instructions, got to certain point, but then I was denied permission.  Now the file is in my user directory but I cannot delete it.  It says I don't own it so I can't remove it.  How can I get rid of this?  I was hoping to use NZB files, but apparently I don't understand the intricacies of python et.al.  Can someone help me get rid of hellanzb?

---

### Post by spamathon on 2006-08-22
> **Ambimom said:**
> Hope someone is still reading this thread....<snip>
You're in luck!

Ok, the guide isn't *perfect*, apparently (but very helpful!); try this for **point 6**:```
sudo python setup.py install
```

Similarly, anything that you "can't do" can be done (usually) by placing a **sudo** in front.  Hence, be very careful when deleting files using *sudo*.  The reason you need to use it here is because these files are being placed into directories that your logged-in user doesn't own or have permission to change.

I'm pretty sure **sudo** means "DO this action as a Super User", but I could be wrong...  Either way, it's handy to think of it that way.  Yep, I'm new to Linux, but thoroughly enjoying it. :)

---

### Post by spock1982 on 2006-08-25
WOW! Thanks this is a great how to. I am now one step closer to ditching my XP installation.

---

### Post by Sawyer on 2006-08-26
> **gurgle said:**
> I would love a guide for installing Sabnzbd. the program itself is easy, its just the dependencies that are a biatch.

Yup. I wonder why Sabnzbd, which is more powerful than HEllaNZB, hasn't been as extensively covered. I can't get it installed, yet some people seem to have so little trouble no one actually bothered making a scant HowTo on it.

Bummer.

---

### Post by chell on 2006-08-28
How do I uninstall this program. Not that I want to but I think I'll sleep better if I do...

Cheers

chell

---

### Post by pipehippy on 2006-08-30
Thanks for the great tute Danalog.  I'm sure it even makes perfect sense to the majoruty of users, unfortunately this first day user is strugglin - It just took me over an hour just to put amsn on my system!

Couple of questions...

Whats going wrong here?

hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(changeme) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: worlds fastest indian
Parsing: worlds fastest indian.nzb...
Parsed: 30 files (5933 posts), 1454.3MB
Queued: 1454.3MB

Also I'm still trying to get my head around this terminal idea, I'm very used to the comfort zone of the setup exec.  If i get the script working do I save it then run it again?  If I do save it how do I re execute it?

Thanks for any possible help

---

### Post by TwoWordz on 2006-08-30
@pipehippy:

Here is how it works:

When you start hellanzb, it checks for new files in the nzb directory and start to download if it finds one.

Once you installed the program, it will stay on your computer. You will need to run it each time you start your session and the console must remain open as long as you want to use hellanzb.

I use gnome-session to start hellanzb automaticly. 

hope this helps,

tw

---

### Post by pipehippy on 2006-08-30
Thanks, sorted it now.  Somebodies useful comment concerning config.sample saved me ***.

---

### Post by TuxCrafter on 2006-09-05
Hello boys i have some problems and hope we can solve them:

I cant download a separate *.nzb file if it is the only one in the *.nzb file i query ( i want to donwload only a nzb file)

for example:
[http://yabse.com/index.php?q=178668](http://yabse.com/index.php?q=178668)

I make a nzb for dowloading that nzb. So that i can query the downloaded nzb after that.

Also. I want hellanzb to do one thing at a time, only par2 -r or unrar or only download. because the system don't like parring unraring en downloading at the same time. (i already set these things in the config file
```

# Disable SMART_PAR (download all PAR files)
Hellanzb.SMART_PAR = False

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = False

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 1

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
#Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]

# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]
```

Can someone help me?

---

### Post by ravpaul on 2006-09-10
Hi guys, I keep getting the following error when running hellanzb.py:

(news2) Opening 4 connections...
hellanzb - Now monitoring queue...

and nothing happens.

I do not know the name of my usenet server or how to obtain it. I am registered with newzbin but do not have any other information at the moment.

I am putting the nzb files into the folder that I have specified in the /usr/etc/hellanzb.conf
 but no use.

Please help, I've paid for 8 weeks and after 2 still have not managed to resolve anything.

---

### Post by TuxCrafter on 2006-09-10
You have to set the correct settings for your news server in the hellanzb config file. adress user and password ect must al be correct.

---

### Post by ravpaul on 2006-09-10
[HTML]You have to set the correct settings for your news server in the hellanzb config file. adress user and password ect must al be correct.[/HTML]

How do I know whast my news server is?

---

### Post by TuxCrafter on 2006-09-10
you have to find this information by your supplyer of your newsserver

---

### Post by theiz on 2006-09-15
I have got quite a fast internet connection (1000KB/s), with Klibido I get download speeds from my newsserver of 800-900KB/s, with hellanzb I have speeds around 75KB/s...

I checked the .conf and there are #-signs before the limiter. Also all 8 connections are used.

Can anyone help me on this?

---

### Post by GuiGuy on 2006-09-21
> **danalog said:**
> 
Happy NZB hunting :)

Hi,
I had followed your instructions and except for some issues with permissions (everything seems to install to root), it was working fine.

Then, yesterday I get this:

> hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(changeme) Opening 8 connections...
hellanzb - Now monitoring queue...
Resuming: <some nzb>
Parsing: <some files>...
Parsed: 18 files (26 posts), 3.8MB
Queued: 3.8MB


it stalls a Queued and nothing happens. <some nzb> is a valid nzb file and <some files> are valid files to be downloaded.

hellanzb.py status shows hellanzb.py is "idle"

I've tried to clear the queue and restart but only get the same result.

Any ideas?

Thanks

---

### Post by GuiGuy on 2006-09-21
> **GuiGuy said:**
> 

hellanzb.py status shows hellanzb.py is "idle"

I've tried to clear the queue and restart but only get the same result.


Nevermind- the damn thing just came good all by itself. I have no idea what's going on... :confused:

---

### Post by GuiGuy on 2006-09-22
> **theiz said:**
> I have got quite a fast internet connection (1000KB/s), with Klibido I get download speeds from my newsserver of 800-900KB/s, with hellanzb I have speeds around 75KB/s...


I've got the same issue - on ADSL  1500/256. KLibido downloads at max speed. Hellanzb < 40kb/s

Thanks

---

### Post by TuxCrafter on 2006-09-23
> **GuiGuy said:**
> Hi,
hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(changeme) Opening 8 connections... !!!!!!!!!
hellanzb - Now monitoring queue...
Resuming: <some nzb>
Parsing: <some files>...

I don't think you have you connection configured the right way check the first post and your server for settings and information.

---

### Post by TuxCrafter on 2006-09-23
I don't now what your speed issue is!

I am looking for more control on the hellanzb process.

I want it to stop checking the par files when it's downloading.
But i can't set that setting in the config file file (only smart par)

Also i want hellanzb to exit when there is nothing to do any more.
So i can use hellanzb better in scripts.

Is there a another program that is command line and downloads only nzb files?

---

### Post by RageAgainstThis on 2006-09-26
I'm a little new to linux and trying to figure out where i went wrong on my configuration file.  It finds the new nzb but does no process it.  Is that an issue with my config file.  I believe i installed it correctly.  Anyhow if anyone could please look over my config file to check


hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(astraweb) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb (msgid: 2122273): Inside_Man_(2006)_(H.264)

code/
# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 726 2006-03-23 18:32:18Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'astraweb',
             hosts = [ 'news.astraweb.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'xxxxxxxx',
             password = 'xxxxxxxx',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/home/branden'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = '/home/branden/NZBQUEUE'

# Where the fully processed archives go
Hellanzb.DEST_DIR = '/home/branden/FINALDESTINATION'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = False

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]
/code

---

### Post by RageAgainstThis on 2006-09-26
Sorry i guess i posted wrong.  I meant to do it by code.

---

### Post by Floor19 on 2006-09-26
For those looking for a installation guide of SABnzbd.

[http://drbyte.wiki.xs4all.nl/index.php?title=drbyte:Community_Portal#Installation_SABnzbd](http://drbyte.wiki.xs4all.nl/index.php?title=drbyte:Community_Portal#Installation_SABnzbd)

Cheers.

---

### Post by TuxCrafter on 2006-09-26
There are a lot of nzb downloaders out there. I now also test nzbperl it as great features that hellanzb doens't have. It only use a slower decoder.

---

### Post by Sawyer on 2006-10-20
> **ravpaul said:**
> Hi guys, I keep getting the following error when running hellanzb.py:

(news2) Opening 4 connections...
hellanzb - Now monitoring queue...

and nothing happens.

I do not know the name of my usenet server or how to obtain it. I am registered with newzbin but do not have any other information at the moment.

I am putting the nzb files into the folder that I have specified in the /usr/etc/hellanzb.conf
 but no use.

Please help, I've paid for 8 weeks and after 2 still have not managed to resolve anything.


LOL!
Newzbin isn't a server. You still need a (paid) server.
Here you go. These are the best in the business:

```
http://www.giganews.com/?c=gn222979
```

The most retention, as in the files that are uploaded will be preserved longer than any other newsservers out there.

$25 monthly.

The .nzb's you generate in newzbin, or yabse, or any other monitor sites, you drop 'em into the "queue" folder you specified in Hellanzb, and off you go. The terminal will notify you of any developments, such as what is downloading or what is unrarring etc. 

Remember, drop just the .nzb file. If I remember correctly, hella doesn't process zip archives the way SAB does.

---

### Post by aztechclan on 2006-11-02
Hi RageAgainstThis,
I've had this problem before, and it has re-occured a couple times.  Hellanzb will decide to kinda sit there and not download anything.  It seems to happen in unusual circumstances and I can't reproduce them.  To fix it, I had to delete the entire hellanzbhome/nzb directory.  That includes the daemon.queue and others.  Hellanzb will recreate it the next time it runs, and your files will download.  You also need to delete and recreate the directory you use for your downloads.  hellanzbhome/usenet I believe.  You can copy the downloads out of there first of course.  

Try it, it'll work I swear.  Not sure why really but I think it's getting it's saved state screwed up somehow.




> **RageAgainstThis said:**
> I'm a little new to linux and trying to figure out where i went wrong on my configuration file.  It finds the new nzb but does no process it.  Is that an issue with my config file.  I believe i installed it correctly.  Anyhow if anyone could please look over my config file to check


hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(astraweb) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb (msgid: 2122273): Inside_Man_(2006)_(H.264)

code/
# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 726 2006-03-23 18:32:18Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'astraweb',
             hosts = [ 'news.astraweb.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'xxxxxxxx',
             password = 'xxxxxxxx',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/home/branden'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = '/home/branden/NZBQUEUE'

# Where the fully processed archives go
Hellanzb.DEST_DIR = '/home/branden/FINALDESTINATION'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = False

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]
/code

---

### Post by jhaquo on 2006-11-07
hi
im using hellanzb since a few days now and its awsome
the problem is, when i make a big nzb with different files, he will only extract them when he has downloaded everything. is there any way to extract the files as ssoon as everything is downloaded for THAT file?

thanks in advance :)

---

### Post by 454redhawk on 2006-11-08
Some Free NZB sites. some may require free registration.

[http://www.nzbpowered.com/](http://www.nzbpowered.com/)

[http://thepeerhub.com/index.php](http://thepeerhub.com/index.php)

[http://nzbmatrix.com/](http://nzbmatrix.com/)

[http://www.newzleech.com/](http://www.newzleech.com/)

[http://www.nzbfile.com/](http://www.nzbfile.com/)

[http://www.tvnzb.com/nzb](http://www.tvnzb.com/nzb)

[http://www.binindex.net/group_search.php](http://www.binindex.net/group_search.php)

[http://www.merlins-portal.net/Vbulletin/forums.php](http://www.merlins-portal.net/Vbulletin/forums.php)

[http://www.newsfix.net/modules.php?name=nzb](http://www.newsfix.net/modules.php?name=nzb)

[http://alt.binaries.nl/](http://alt.binaries.nl/)

---

### Post by DragonZeal on 2006-11-11
Hi I'm using Kubuntu 6.10.

I'm unable to install rar or par2.
dragonzeal@dragonzeal-desktop:/usr/etc$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

Can anybody help?

---

### Post by TuxCrafter on 2006-11-11
> **DragonZeal said:**
> Hi I'm using Kubuntu 6.10.

I'm unable to install rar or par2.
dragonzeal@dragonzeal-desktop:/usr/etc$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

Can anybody help?

Try this :-D
sudo apt-get install rar par2

---

### Post by DragonZeal on 2006-11-11
Trying  to be funny?
dragonzeal@dragonzeal-desktop:/usr/etc$ sudo apt-get install rar par2
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

---

### Post by TuxCrafter on 2006-11-11
hmm strange i will try a vmware image with edgy

---

### Post by TuxCrafter on 2006-11-11
Can you install other things?

---

### Post by DragonZeal on 2006-11-11
I'm trying Ubuntu now instead of Kubuntu.

Installing rar and par2 works.

Is it a problem with Kubuntu?

---

### Post by TuxCrafter on 2006-11-11
Bug comfirmed, I have a clean xubuntu edge vmware install, enabled universe multiverse ect. Did a nice update an upgrade. and tried to install rar and unrar but the packages are not found.

Maybe you can download and compile rar manually.

---

### Post by TuxCrafter on 2006-11-13
I have been working on the problem, could you try to change the locations in your source list.

---

### Post by TuxCrafter on 2006-11-14
emmm.. seems i forgot to enable the compleet multiverse repos. 
you have to make realy sure multiverse is enabeld :-D

Problems, solved there is no bug. I had to been really sure that 
multiverse was enabled and the sources.list had the right structure. I 
think some small things in the source.list structure have changes, in 
the right way I might say. It now only takes one line for al the 
packages and one line for al the sources.

---

### Post by leogibson on 2006-11-17
ok, first i tried the OPs way...figured out i needed multiverse.  ok.  then had some trouble remembering to use sudo...ok.  WOW heres a .deb from jason!!...seems to have been installed...im a real noob, but wheres the program?  i try running hella.py and whatnot, and you guessed it...nothing. the Edgy deb manager says its installed fine...but i dont see a program running, or where to click on hella in the top bar???  do i need to be logged in as root?  whats the deal? im totally lost.  this was the one reason i was still using XP...now im really frustrated

root@leo-laptop:~# hellanzb.py
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in ?
    from Hellanzb.Core import main
  File "/usr/share/hellanzb/Hellanzb/Core.py", line 9, in ?
    from Hellanzb.HellaReactor import HellaReactor
  File "/usr/share/hellanzb/Hellanzb/HellaReactor.py", line 11, in ?
    import twisted.copyright
ImportError: No module named twisted.copyright

What am i doing wrong here????  what should i edit?
HELP

matt](*,) :-k :confused: ](*,)

---

### Post by TuxCrafter on 2006-11-17
How did you install Hellanzb? Can you give me al the steps.

---

### Post by leogibson on 2006-11-17
first, i tried the initial way on the original post. i downloaded hellanzb-0.9.tar.gz, and tried to install that way, using the exact code, and i edited my config file just like the 1st post said. might not have deleted all that before i tried the deb package..how do i remove everything and start over from scratch?

thanks for your help

---

### Post by TuxCrafter on 2006-11-17
Hmm. I have not yet testet 0.9 release. In the readme of the source there is info on how to install and deinstall.

---

### Post by kaath on 2006-11-17
0.10 is out
[http://www.hellanzb.com/distfiles/hellanzb-0.10.tar.gz](http://www.hellanzb.com/distfiles/hellanzb-0.10.tar.gz)

---

### Post by leogibson on 2006-11-17
the readme says nothing about how to uninstall.:-k

---

### Post by TuxCrafter on 2006-11-17
You lucky basterd i will make a script for you :-D

---

### Post by TuxCrafter on 2006-11-17
```
#Company:	PowerCraft Technology
#Author: 	Copyright Jelle de Jong <jelledejong@powercraft.nl>
#Version:	0.0.2
#Date:		20-07-2006 / 17-11-2006
#System:	Xubuntu 6.06
#Description:	Setting up hellanzb
#Information:	http://www.ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb
#Information:	http://www.hellanzb.com/
#Command:	sudo ~/scripts/installations/hellanzb.sh

# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.

#!/bin/sh

sudo apt-get install python-dev python-twisted unrar par2

wget http://www.hellanzb.com/distfiles/hellanzb-0.10.tar.gz
tar -xzvf hellanzb-0.10.tar.gz

cd hellanzb-0.10/
sudo python setup.py install

sudo chmod 666 /var/tmp/hellanzb.log

wget http://www.hellanzb.com/hellanzb-content/yenc-0.3.tar.gz
tar xzfv yenc-0.3.tar.gz
cd yenc-0.3
python setup.py build
sudo python setup.py install

#grep -n ^defineServer /usr/etc/hellanzb.conf | grep -o ^[[:digit:]]*
#grep -n ")" /usr/etc/hellanzb.conf | grep -o ^[[:digit:]]*

exit

```

I want to know how it works out :-P

you still need to configure the hellanzb config file

sudo cp ~/scripts/installations/hellanzb/hellanzb.conf /usr/etc/hellanzb.conf

---

### Post by leogibson on 2006-11-18
thanks for the script, it worked great, but the reason it wouldnt start was...my noobage.  it never says to type ./ infront of a script anywhere in this thread to run it...ive read though quite a bit of the ubuntu documentation, i guess i just dont know the basics 100% yet.

thank you jason, and thank you for the script, tux.

---

### Post by saffsd on 2006-12-10
Hello everyone! I've hacked on the script for autorunning hellanzb above a bit, and here's my version of it:

```

#! /bin/bash
#
# hellanzb       Start the hellanzb.
#


NAME=hellanzb
NNTPS_SERVER=your_newsserver
NNTPS_PORT=563
USERNAME=your_username
STUNNEL_PIDFILE=/var/run/stunnel/stunnel.$NNTPS_SERVER.$NNTPS_PORT.pid
HELLANZB_PIDFILE=/var/run/hellanzb.pid

trap "" 1
export LANG=C

case "$1" in
  start)
    echo -ne "Starting $NAME"
    start-stop-daemon -S --pidfile $STUNNEL_PIDFILE --exec /usr/bin/stunnel -- -s $USERNAME -c -d localhost:119 -r $NNTPS_SERVER:$NNTPS_PORT
    echo -ne "."
    start-stop-daemon -S -c $USERNAME -m -b --pidfile $HELLANZB_PIDFILE --exec /usr/bin/screen -- -S $NAME -D -m /usr/bin/python /usr/bin/hellanzb.py 
    echo "."
    ;;

  stop)
     echo -ne "Stopping $NAME"
     start-stop-daemon -K --pidfile $STUNNEL_PIDFILE
     echo -ne "."
     start-stop-daemon -K --pidfile $HELLANZB_PIDFILE
     echo "."
    ;;
  
  restart)
    $0 stop
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/$NAME start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

I'm pretty much a BASH noob so it's not a very good script, could still use alot of work (like properly handling if stuff is already running). At least it drops both stunnel and hellanzb to user-level privilleges.

Hellanzb needs to be set up properly for this script to work. Id est, you should be able to use it by keying "hellanzb.py" at the prompt.

I'm also not 100% sure it will work for everybody, please post results if you try it. Also, this script is for SSL-enabled nntp, hence it opens and closes and stunnel tunnel as needed. Could make this optional if anyone desires, i just happen to use it. screen -R hellanzb works. NOTE: you will need to use stunnel3 with this script. I used stunnel3 in the repos, stunnel4 in the repos was buggy (its not the latest version. the latest version doesnt have the same problem, but i cant find a deb for it).

---

### Post by supertux on 2007-01-02
Hi, i changed that init script also a bit, it works for me now, including the screen functionality..

```

#! /bin/bash
#
# hellanzb       Start the hellanzb.
#
# hellanzb init-script v0.5
#
# the following vars are used:
# NAME= leave it to hellanzb, its just a display name and it is used to connect to it with screen
# USERNAME= your username, this is used to run hellanzb in
# HELLANZB_PIDFILE= the pid file which the script checks
#
#



NAME=hellanzb
USERNAME=<your username>
HELLANZB_PIDFILE=/var/run/hellanzb.pid

trap "" 1
export LANG=C

case "$1" in
  start)
    echo -ne "Starting $NAME"
    start-stop-daemon -S -c $USERNAME -m -b --pidfile $HELLANZB_PIDFILE --exec /usr/bin/screen -- -S $NAME -D -m /usr/bin/python /usr/bin/hellanzb.py
    echo "."
    ;;

  stop)
     echo -ne "Stopping $NAME"
     start-stop-daemon -K --pidfile $HELLANZB_PIDFILE
     echo "."
    ;;

  restart)
    $0 stop
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/$NAME start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

So change the USERNAME var. and start it.. When its working you can add it to the required runlevels!

---

### Post by yezzer on 2007-01-04
I havent time to read the entire thread (too long!)
but i found when i installed this I had to:

6. python setup.py install
change
6. sudo python setup.py install

8. sudo gedit /usr/etc/hellanzb.conf.sample 
change
8. sudo gedit /usr/etc/hellanzb.conf

otherwise you're editing the sample file.

Note: i'm completely new to this, so i may have done everything wrong.. but it DOES work for me! :D

---

### Post by kd7swh on 2007-01-12
Can anyone show me how to add ssl support with stunnel or sslwrap?

---

### Post by frolle on 2007-01-18
Anybody how got zussaweb working? Its a great webui.

---

### Post by shadowuht on 2007-01-22
> **kd7swh said:**
> Can anyone show me how to add ssl support with stunnel or sslwrap?

I would appreciate this too.

---

### Post by VuDu on 2007-01-25
> **leogibson said:**
> ok, first i tried the OPs way...figured out i needed multiverse.  ok.  then had some trouble remembering to use sudo...ok.  WOW heres a .deb from jason!!...seems to have been installed...im a real noob, but wheres the program?  i try running hella.py and whatnot, and you guessed it...nothing. the Edgy deb manager says its installed fine...but i dont see a program running, or where to click on hella in the top bar???  do i need to be logged in as root?  whats the deal? im totally lost.  this was the one reason i was still using XP...now im really frustrated

root@leo-laptop:~# hellanzb.py
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in ?
    from Hellanzb.Core import main
  File "/usr/share/hellanzb/Hellanzb/Core.py", line 9, in ?
    from Hellanzb.HellaReactor import HellaReactor
  File "/usr/share/hellanzb/Hellanzb/HellaReactor.py", line 11, in ?
    import twisted.copyright
ImportError: No module named twisted.copyright

What am i doing wrong here????  what should i edit?
HELP

matt](*,) :-k :confused: ](*,)

I'm having the same problem... I have just installed python-twisted and hellanzb, and I get this:

```
vudu@vudumachine:~$ hellanzb 
Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/var/lib/python-support/python2.5/Hellanzb/Core.py", line 12, in <module>
    import optparse, os, signal, sys, time, thread, threading, Hellanzb, Hellanzb.PostProcessor
  File "/var/lib/python-support/python2.5/Hellanzb/PostProcessor.py", line 15, in <module>
    from Hellanzb.PostProcessorUtil import *
  File "/var/lib/python-support/python2.5/Hellanzb/PostProcessorUtil.py", line 13, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize
```

I dunno what to do.. I'm on Feisty by the way.

---

### Post by Roderik on 2007-01-28
```
roderik@alucius ~ $ hellanzb.py 
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 12, in <module>
    import optparse, os, signal, sys, time, thread, threading, Hellanzb, Hellanzb.PostProcessor
  File "/usr/lib/python2.5/site-packages/Hellanzb/PostProcessor.py", line 15, in <module>
    from Hellanzb.PostProcessorUtil import *
  File "/usr/lib/python2.5/site-packages/Hellanzb/PostProcessorUtil.py", line 13, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

```

i've got the same problem on a new feisty install

there was also a prolem when installing, but that was solved by installing python2.5-dev

---

### Post by Roderik on 2007-01-28
just found a matching bug report in the hellanzb trac, testing the svn version now

[http://www.hellanzb.com/trac/hellanzb/ticket/254](http://www.hellanzb.com/trac/hellanzb/ticket/254)

UPDATE: svn version works like expected!

---

### Post by Duffman on 2007-01-28
Wow thanks alot man this really is nice. Definitely one of the reasons i was still using windows... Now if we could get a nice gui for it

---

### Post by kd7swh on 2007-01-30
There are some GUIs out there for it.

---

### Post by pirothezero on 2007-02-07
I can't move nzb files to daemon.queue, i keep getting:

cp: cannot create regular file `/giganews/nzb/daemon.queue': No such file or directory

the directory is there so no idea what is going on.  And when i try to drag it in I get access denied. 

My permissions screwed up?

---

### Post by kd7swh on 2007-02-10
> My permissions screwed up?

Most likely yes.

try doing a "chmod 777" to the directory. (as root)

---

### Post by BigB3n on 2007-02-10
Great forum here, it already helped me several times.
I find hellanzb really a top program. However I have a litle problem:
After creating the /downloadddir/usenet/MYDOWNLOADNAME.
It has the permition root root 755. Can is automatic change this (not with chmod because the the next time I have the same problem)? Because the map /downloaddir/usenet is shared by samba so i have to be able to modify this map and its content.

Thanks

---

### Post by kd7swh on 2007-02-10
> **BigB3n said:**
> Great forum here, it already helped me several times.
I find hellanzb really a top program. However I have a litle problem:
After creating the /downloadddir/usenet/MYDOWNLOADNAME.
It has the permition root root 755. Can is automatic change this (not with chmod because the the next time I have the same problem)? Because the map /downloaddir/usenet is shared by samba so i have to be able to modify this map and its content.

Thanks


I don't know about automatically changing it, but you can run hellanzb as root. 

```
sudo hellanzb.py
```

This would give you all the needed permissions. Permissions are the reason I don't use Samba. Maybe you can change the permission in the samba.conf file that might retain it. (just a thought) 

good luck! :)

---

### Post by satrich on 2007-02-13
I have a question about hellanzb. It is running fine here.
But the question is, does Hellanzb reconnect to the newsserver after a connection time-out? Because my newsserver gives me time-outs every time I reach my monthly downloadlimit. But I can download in Windows with Grabbit after reaching that limit. Grabbit just keep trying to reconnect and after some time it will connect again and start downloading.

Is there such a feature in Hellanzb as reconnect to the server after a connection time out? It just seems like it hangs now. It just have to keep trying to connect to the server, but does it do that?

EDIT:
Well, I noticed that the download is continuing after a while. So the time-outs are handelled. But is there a parameter that can be set for this, so that Hellanzb will try to connect more often?
I see an option antiIdle = 4.5 * 60 in the hellanzb.conf file. I am wondering what antIdle does?

---

### Post by kd7swh on 2007-02-14
> **satrich said:**
> I have a question about hellanzb. It is running fine here.
But the question is, does Hellanzb reconnect to the newsserver after a connection time-out? Because my newsserver gives me time-outs every time I reach my monthly downloadlimit. But I can download in Windows with Grabbit after reaching that limit. Grabbit just keep trying to reconnect and after some time it will connect again and start downloading.

Is there such a feature in Hellanzb as reconnect to the server after a connection time out? It just seems like it hangs now. It just have to keep trying to connect to the server, but does it do that?

EDIT:
Well, I noticed that the download is continuing after a while. So the time-outs are handelled. But is there a parameter that can be set for this, so that Hellanzb will try to connect more often?
I see an option antiIdle = 4.5 * 60 in the hellanzb.conf file. I am wondering what antIdle does?

I have not really had any problems like this. (but I have unlimited bandwidth). I figure that antiIdle is the key. 60 is most likely seconds (in this case 60 is one minute) and that is being multiplied by 4.5. So it will attempt to reconnect every 4.5 minutes??? 

(Thats how I read it.)

play around with it and let me know what works for you.

Good Luck!

---

### Post by kditty on 2007-02-15
im having a problem with my config file. i recently switched news servers, and now i am using  newsdemon instead of unsenetserver, how do i go about changing this in my settings to allow me to download from newsdemon instead?

---

### Post by shookone on 2007-02-16
I have been using Hellanzb for some time. I think its great... this thread is great, as it has helped me discover this great app.

However, I'm noticing that this application is starting to stop after a parity check. I don't see errors, Process list shows that it is trying to unrar the files but there is no activity.

Please help me .. I'm using some script someone set up to get hellanzb to work via screen from this thread.

---

### Post by pirothezero on 2007-02-16
> **shookone said:**
> I have been using Hellanzb for some time. I think its great... this thread is great, as it has helped me discover this great app.

However, I'm noticing that this application is starting to stop after a parity check. I don't see errors, Process list shows that it is trying to unrar the files but there is no activity.

Please help me .. I'm using some script someone set up to get hellanzb to work via screen from this thread.

I started having the same problem. I took the advice on a few pages back and pulled anything completed out of usenet and deleted usenet and the nzb directory and restarted my comp. and it created nzb and usenet again.

Then i ran the same file I had tried to get and it did it again. Then I come across the php module Zussaweb and I came across the commands hellanzb.py status and hellanzb.py shutdown which I was to ignorant to try/read the man for. After doing both and restarting it again with sudo hellanzb.py it processed the finished file it had stored in .processing which is where I was getting stuck and queued up the next one. Will report back if it hangs again. 

Another thing, so outside of the screen -R hellanzb is there anyway to get a console of hellanzb processing ? Outside of shutting down the processing and starting it back up again. The screen method like reported for someone else doesn't do anything for me.

---

### Post by disturbedite on 2007-02-20
i'm completely new to newsgroups and what not.  hellanzb seems really simple so i like it.  but i'm having the same problem as the guy a couple pages back.  its thats nothing happens once hellanzb  gets to to a certain point:
hellanzb v0.12 (config = /usr/etc/hellanzb.conf)
(news.qwest.net) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: 1171952904
Parsing: 1171952904.nzb...
Parsed: 1 files (18 posts), 6.8MB
Queued: 6.8MB
[1]
[2]
[3]
[4]
[Total] 0.0KB/s, 6 MB queued, ETA: 00:00:0

i tried it with several nzb files from yabse including one that is only a day old but nothing works, it just sits there.  i also tried deleting those directories in ~/ and letting hellanzb regenerate them itself, but that didn't work either.
here is my config file:
# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 994 2007-01-31 10:25:07Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'news.qwest.net',
             hosts = [ 'news.qwest.net:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = '**********',
             password = '********',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 3.0 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0             # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/home/disturbedite/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'usenet/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
#Hellanzb.PAR2_CMD = None

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = False

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'

could someone help me out please?

---

### Post by pirothezero on 2007-02-20
have you tired hellanzb.py shutdown and starting it again.

---

### Post by disturbedite on 2007-02-20
wow that was a quick reply.  thanks.  i didn't think that'd work since i assumed i closed hellanzb correctly, but i tried it anyway and got:
Unable to connect to XMLRPC server,
error: Connection was refused by other side: 111: Connection refused.
The hellanzb queue daemon @ [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760) probably isn't running

as it sounds, i'm pretty sure that just means it isn't running at the time the command was executed.

btw, i forgot to mention that i also tried running it as root but that didn't work either.

---

### Post by shookone on 2007-02-20
> **pirothezero said:**
> I started having the same problem. I took the advice on a few pages back and pulled anything completed out of usenet and deleted usenet and the nzb directory and restarted my comp. and it created nzb and usenet again.

Then i ran the same file I had tried to get and it did it again. Then I come across the php module Zussaweb and I came across the commands hellanzb.py status and hellanzb.py shutdown which I was to ignorant to try/read the man for. After doing both and restarting it again with sudo hellanzb.py it processed the finished file it had stored in .processing which is where I was getting stuck and queued up the next one. Will report back if it hangs again. 

Another thing, so outside of the screen -R hellanzb is there anyway to get a console of hellanzb processing ? Outside of shutting down the processing and starting it back up again. The screen method like reported for someone else doesn't do anything for me.

debug?

I think debug is all we got. I actually think its the screen thats stopping the processing. Its strange because it stops the processing when par2's complete 100%.. unrar loads up and doesn't do anything.

I'm going to try and run this without screens see if that helps. Im running this app from init.d/script that i got from this thread so it maybe that its causing this processing part to freeze.

---

### Post by ghoti on 2007-02-21
Hi Just thought Id add my 2 cents to this.

First off, a big thanks for all the people who have contributed to this subject, thanks to you I am now running hellanzb, and am using the zussaweb frontend happily.

The methods I used were:
installed the hellanzb system as per the original howto, chaned the /etc/init.d/hellanzb script to the per user one.
Installed zussaweb (fixing a few typos in the sourcecode)

the main error I had was from the write permissions on the daemon.queue folder, which needed to be "chmod o+w daemon.queue" so that zussaweb could upload the files.

Next mission for me is to see if i can get this to work wholly from the one webpage, so i can start, stop and play to my hearts content.

---

### Post by disturbedite on 2007-02-22
this is prolly gonna sound like a really stupid question, cuz i think its prolly so easy that i'm overlooking how to do it, but how do you install zussaweb?

just extract the archive somewhere then what?

UPDATE:  i finally got hellanzb working, sorta.  i realized i was trying to use the wrong news server.  my isp is qwest w/ msn premium.  i was trying to use qwest's news servers when i should have been using msn's.  so now thats what i'm trying to use.  (msnews.microsoft.com:119).  but now EVERY time i drop a nzb file in the queue folder i get:

Found new nzb: 1172265153
Parsing: 1172265153.nzb...
Parsed: 1 files (1 posts), 90KB
Queued: 90KB
hellanzb-tmp-1172265153.file0001 segment: 1 Article is missing!
Transferred <1KB in 0s at 0.4KB/s (1172265153)
1172265153: Finished processing (took: 0s) (total: 0s) (No Pars)

i'd appreciate any help.

---

### Post by pirothezero on 2007-03-03
I am just going to say it..i don't mean to crap thread if it's considered as such.

I moved over from hellanzb to sabnzbd because I kept getting errors in the running of hella when it was downloading stuff and would leave stuff partially processed and i'd have to go in and either download the remaining files myself and extract it or just extract it. I deleted folders, reinstalled, upgraded, did everything i could think of but it kept throwing exceptions in hellanzb.py status.

After the move I couldn't be more happy.

---

### Post by Roderik on 2007-03-04
I noticed that the latest release crapped out on me very often. First i thought that the python 2.5 on feisty was the cause but on edgy it was the same misery all over again. So i also moved to sabnzb and am happy with it for now. Allthough i don't like it eating all nzb's instead of only the one it's working on, and i am not particulary fond of a webbased userinterface. But hey at least i'm leeching again :)

---

### Post by TuxCrafter on 2007-03-04
New Versions have come out so i created a new version of my script:

Have fun and report your feedback please :-D

---

### Post by giruzz on 2007-03-07
```
[-] Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/usr/lib/python2.4/site-packages/Hellanzb/NZBLeecher/__init__.py", line 231, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.4/site-packages/twisted/internet/posixbase.py", line 218, in run
    self.mainLoop()
  File "/usr/lib/python2.4/site-packages/twisted/internet/posixbase.py", line 226, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.4/site-packages/twisted/internet/base.py", line 555, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.4/site-packages/Hellanzb/NZBLeecher/Protocol.py", line 505, in fetchNextNZBSegment
    self.deactivate()
  File "/usr/lib/python2.4/site-packages/Hellanzb/NZBLeecher/Protocol.py", line 469, in deactivate
    self.factory.deactivateClient(self, justThisDownloadPool)
  File "/usr/lib/python2.4/site-packages/Hellanzb/NZBLeecher/Protocol.py", line 211, in deactivateClient
    endDownload()
  File "/usr/lib/python2.4/site-packages/Hellanzb/Daemon.py", line 304, in endDownload
    downloadTime = time.time() - sessionStartTime
exceptions.TypeError: unsupported operand type(s) for -: 'float' and 'NoneType'

1173097271: Finished processing (took: 0s) (total: 0s) (No Pars)

```

I got this message every time hellanzb finishes with a download and after that crashes.

Any suggestions?

byee

g.

---

### Post by inmazer on 2007-03-16
I have the exact same problem. Something wrong with the new version of hella or something wrong with my set up? This seems to happen only when unraring.

---

### Post by psyduck on 2007-03-19
does anyone know how to uninstall hellanzb? I got the same problem with version 12 as the previous poster, and i want to try an older version

---

### Post by psyduck on 2007-03-19
never mind

---

### Post by Mithrilhall on 2007-03-23
To anyone posting here about the problems they are having could you please post the version of E/K/U/X/buntu and hellanzb that you are running.


Thank you.

---

### Post by giruzz on 2007-03-23
> **Mithrilhall said:**
> To anyone posting here about the problems they are having could you please post the version of E/K/U/X/buntu and hellanzb that you are running.


Thank you.


Kubuntu 6.10 - Hellanzb 0.12

giruz

---

### Post by giruzz on 2007-04-01
A new version is out! :-)

0.13

g.

---

### Post by goonies on 2007-04-01
is anyone maintaining a repository with these packages?

---

### Post by TuxCrafter on 2007-04-01
Updated my installation script for all ubuntu distros

```

#!/bin/bash

#Author: 		Copyright Jelle de Jong <jelledejong@powercraft.nl>
#Note:			Please send me an email if you enhanced the script
#Version:		0.0.6
#Date:			20-07-06 / 17-11-06 / 15-12-06 / 04-03-07 / 17-03-07 / 01-04-07
#System:		Xubuntu 7.04
#Description:		Setting up hellanzb
#Information:		http://www.ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb
#Information:		http://www.hellanzb.com/
#Command:		chmod +x hellanzb.sh; ./hellanzb.sh

# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.

location="$PWD"

echo -n "install the necessary tools [Y/n]? "
read input
if [ "$input" != "n" ]
then
	sudo apt-get install python-dev python-twisted unrar par2 build-essential
fi

echo -n "install hellanzb[Y/n]? "
read input
if [ "$input" != "n" ]
then
	cd ~
	wget http://www.hellanzb.com/distfiles/hellanzb-0.13.tar.gz
	tar -xzvf hellanzb-0.13.tar.gz
	cd hellanzb-0.13/
	sudo python setup.py install

	wget http://www.hellanzb.com/hellanzb-content/yenc-0.3.tar.gz
	tar xzfv yenc-0.3.tar.gz
	cd yenc-0.3
	python setup.py build
	sudo python setup.py install

	cd ~
	rm hellanzb-0.13.tar.gz
	sudo rm -rf hellanzb-0.13
fi

echo -n "set-up personal configuration file for hellanzb[Y/n]? "
read input
if [ "$input" != "n" ]
then
	cd "$location"
	sudo cp hellanzb/hellanzb.conf /usr/etc/hellanzb.conf
	if [ -e /var/tmp/hellanzb.log ] 
	then
		sudo chmod 0666 /var/tmp/hellanzb.log
	fi
fi

#grep -n ^defineServer /usr/etc/hellanzb.conf | grep -o ^[[:digit:]]*
#grep -n ")" /usr/etc/hellanzb.conf | grep -o ^[[:digit:]]*

exit

```

---

### Post by Jongi on 2007-04-09
> **psyduck said:**
> never mind

How did you do it?

---

### Post by Malik on 2007-04-20
malik@malik-desktop:~$ hellanzb.py 
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
ImportError: No module named Hellanzb.Core



wtf is going on?

---

### Post by frolle on 2007-04-22
> **Malik said:**
> malik@malik-desktop:~$ hellanzb.py 
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
ImportError: No module named Hellanzb.Core



wtf is going on?

Good question. I am getting an error a lot the same: 

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 12, in <module>
    import optparse, os, signal, sys, time, thread, threading, Hellanzb, Hellanzb.PostProcessor
  File "/usr/lib/python2.5/site-packages/Hellanzb/PostProcessor.py", line 15, in <module>
    from Hellanzb.PostProcessorUtil import *
  File "/usr/lib/python2.5/site-packages/Hellanzb/PostProcessorUtil.py", line 13, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

---

### Post by sizzam on 2007-04-22
> **frolle said:**
> Good question. I am getting an error a lot the same: 

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 12, in <module>
    import optparse, os, signal, sys, time, thread, threading, Hellanzb, Hellanzb.PostProcessor
  File "/usr/lib/python2.5/site-packages/Hellanzb/PostProcessor.py", line 15, in <module>
    from Hellanzb.PostProcessorUtil import *
  File "/usr/lib/python2.5/site-packages/Hellanzb/PostProcessorUtil.py", line 13, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

I was having the same problem with hellanzb installed from source on a fresh install of Feisty.   Here is how I fixed it:

hellanzb is now in the repositories.

First, I got rid of the copy of hellanzb that I installed:
```

$ sudo rm /usr/bin/hellanzb.py
$ sudo rm -rf /usr/lib/python2.5/site-packages/Hellanzb/
$ sudo rm /usr/etc/hellanzb.*

```
I then installed hellanzb from the repos.   Note that if you are doing a fresh install from the repos, you also need unrar and par2.

```
$ sudo aptitude install hellanzb unrar par2
```

I then executed hellanzb from a command line

```
$ hellanzb
```

and it worked.  After that, I killed hellanzb and configured it.   Note that your configuration file is now /etc/hellanzb.conf instead of /usr/etc/hellanzb.conf

Now I use this command to start hellanzb using screen whenever I log into Gnome:

```
screen -S hellanzb -d -m hellanzb
```

and I use this shortcut in Gnome to connect to that screen (make a custom shortcut with type 'Application in Terminal'):

```
screen -R hellanzb
```

---

### Post by frolle on 2007-04-22
Wow, your my hero :) Thanks a lot, it worked out!

:guitar: :popcorn: :KS

---

### Post by kunchi on 2007-04-26
Thanks Sizzam for the how to in fiesty fixed the errors and runs nicely 

think I can try some more with it but think I have found one more thing linux can do that my xp box did!

now to get CoH working in WINE and I can have linux as my primary os machine

note:
if you are not changing the conf file to allow automatic unrar it will stop at done with the .rar files in the the done directory.
you need to make these changes for automatic unrar to run:
# Supply a path to the (un)rar command
Hellanzb.UNRAR_CMD = '/usr/bin/unrar'

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = True

---

### Post by robertpolson on 2007-05-23
Can you please elaborate on this as when I enter screen -S hellanzb -d -m hellanzb   into the terminal, nothing happens.

Also, with the version from repositories, the older one there is no SSL encryption and this sucks.

---

### Post by kraymore on 2007-05-26
what do i do at this point ?  i've never used nzb or newzbin before.  what does a newzbin subscription do ?  

hellanzb v0.10 (config = /etc/hellanzb.conf)
Hellanzb.XMLRPC_PORT = None, not starting the XML-RPC server
(changeme) Opening 10 connections...
hellanzb - Now monitoring queue...

---

### Post by kraymore on 2007-05-26
i think i understand now.  it only downloads nzb groups of files.  there are alot of other files that are missing nzb's though.  a pity.  

i am curious does it place each nzb in a folder of its own ?  

also how much is 4 weeks premium service in USD ?  

thank you

---

### Post by kraymore on 2007-05-26
i'm getting this error from hellanzb

@ubuntu:~/Desktop$ hellanzb abnl-cc199cae9841f17ea52e0083302b3cfb.nzb
Exiting: FatalError'>: Invalid remote call: abnl-cc199cae9841f17ea52e0083302b3cfb.nzb

is a XML_RPC server necessary ?  i dont know what that is or how to configure it.

---

### Post by phro on 2007-05-26
I think the command you're looking for kraymore is ~$hellanzb.py enqueue some_kinda.nzb

---

### Post by robertpolson on 2007-05-27
> **kraymore said:**
> i think i understand now.  it only downloads nzb groups of files.  there are alot of other files that are missing nzb's though.  a pity.  

i am curious does it place each nzb in a folder of its own ?  

also how much is 4 weeks premium service in USD ?  

thank you

Don't ask here, read on newzbin site [http://docs.newzbin.com/index.php/Main_Page](http://docs.newzbin.com/index.php/Main_Page)

---

### Post by benchMarc on 2007-06-08
Works perfect!

Is it normal that hellanzb uses around 30-50% of cpu load? Looks a bit much to me and it really slows my system down while downloading. It also uses around 26mb of memory.

-- After thinking: maybe it's because i can download around 8MB/s here at school :P And my laptop has a 4200rpm harddisk.

---

### Post by chalewa on 2007-06-09
I seem to be struggling a little bit with this.. I really like it, and i think that it is a great program, i just think that i am missing something. if anyone could help, it would be greatly appreciated..

when i download a nzb and place it in the queue things work great,it downloads to the specified directory, but then nothing more happens, no parity checking, no unraring nothing... Then, if i try to place another nzb in the queue to download next, hellanzb will recognize that it is there, it just won't do anything with it.  even if i delete the old nzb, and only the new on is in the queue, the same thing happens.

here is the output i get when it has finished downloading one nzb


```
chalewa4bambu@chalewad:~$ hellanzb

hellanzb v0.10 (config = /etc/hellanzb.conf)
(changeme) Opening 8 connections...
hellanzb - Now monitoring queue...
Found new nzb: selected_reports_20070608-001240
Resuming: selected_reports_20070608-001240
Parsing: selected_reports_20070608-001240.nzb...
Skipping pars.. (Skipped par2: original-hot.vol000+01.PAR2 (1MB))
Parsed: 323 files (45932 posts), 14902.5MB
Skipped (on disk): 290 files and 33 segments, 13900.5MB
Skipped pars: 33 files, 1017.1MB (actual skipped: 1002.0MB)
 FEST.vol000+01.PAR2 ->
 FEST.vol159+19.PAR2 (13 files, 468.7MB, 178 blocks)
 method-bsmoan.vol000+01.PAR2 ->
 method-bsmoan.vol134+32.PAR2 (10 files, 258.9MB, 166 blocks)
 original-hot.vol000+01.PAR2 ->
 original-hot.vol124+27.PAR2 (10 files, 289.5MB, 151 blocks)
selected_reports_20070608-001240: Assembled archive!

```

the only way that i can get past this is to actually close out the terminal window

Secondly, I cannot get the program to check parity and unrar. I thought that i had my config file done the right way but maybe not...

```
# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 801 2006-07-27 04:11:01Z alex $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'changeme',
             hosts = [ 'unlimited.newshosting.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'xxxxxxxxxxx',
             password = 'xxxxxxxxxxx',
             #username = None,           # no auth
             #password = None,

             connections = 8,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/media/sda2/chalewa4bambu/Network'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = '/media/sda2/chalewa4bambu/Network'

# Where the fully processed archives go
Hellanzb.DEST_DIR = '/media/sda2/chalewa4bambu/Network'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = '/media/sda2/chalewa4bambu/Network'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = '/media/sda2/chalewa4bambu/Network'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = '/media/sda2/chalewa4bambu/Network/Postponed'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = '/media/sda2/chalewa4bambu/Network/Processed'

# Temp storage
Hellanzb.TEMP_DIR = '/media/sda2/chalewa4bambu/Network/TEMP'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = '/media/sda2/chalewa4bambu/Network/XML'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = '/media/sda2/chalewa4bambu/Network/Processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

# Disable SMART_PAR (download all PAR files)
Hellanzb.SMART_PAR = True

# Supply a path to the (un)rar command
Hellanzb.UNRAR_CMD = '/usr/bin/unrar'

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = False

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to http://www.newzbin.com for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'
```


Any ideas? Thanks guys

---

### Post by xadloki on 2007-06-11
Hello, I'm trying to go by this guide and there's an error I'm getting at the "python setup.py install" step...

xad@Kubuntu:~/hellanzb-0.13$ python setup.py install
running install
running build
running build_py
creating build
error: could not create 'build': Permission denied

I'm using Kubuntu 7.04
Thanks for this guide and hope someone can give me a hint to what I'm doing wrong...

Ah nevermind... I typed "sudo python setup.py install" and it worked, though I did try that before but I probably misstyped sudo :P

---

### Post by giruzz on 2007-06-11
> **xadloki said:**
> Hello, I'm trying to go by this guide and there's an error I'm getting at the "python setup.py install" step...

xad@Kubuntu:~/hellanzb-0.13$ python setup.py install
running install
running build
running build_py
creating build
error: could not create 'build': Permission denied

I'm using Kubuntu 7.04
Thanks for this guide and hope someone can give me a hint to what I'm doing wrong...

sudo python setup.py install

g.

---

### Post by cchester on 2007-06-14
Hi,

Is there a gui that works for this and if so how do you install it and run it.

Thanks

---

### Post by honeydew on 2007-06-26
> **cchester said:**
> Hi,

Is there a gui that works for this and if so how do you install it and run it.

Thanks

I just wrote a python script that works with conky(will work in gnome/kde/xfce), it may work out for you.. I use this and hellafox and all my needs are met.

here is a howto
[hellaconk]("http://wiki.arcintel.com/doku.php?id=hellaconk")
[http://ubuntuforums.org/showthread.php?t=483774]("http://ubuntuforums.org/showthread.php?t=483774") 

I also attached a screenshot....

---

### Post by TuxCrafter on 2007-06-26
> **cchester said:**
> Hi,

Is there a gui that works for this and if so how do you install it and run it.

Thanks

There is no real gui for hellanzb yet. however you can try sa

sabnzbd hellanzb klibido pan nzbget nzbpower knzb slurp ubh < all linux usenet binary downloaders

My favorites are sabnzbd and hellanzb

sabnzbd has a very nice website gui system I recommend that one for you. Search the forum for installation help.

---

### Post by cchester on 2007-06-26
Thanks TuxCrafter for the info and recommendations.

Thanks honeydew for the script.

---

### Post by NeoTaoistTechnoPagan on 2007-07-11
Wow! I absolutely love this!

Now it's a good thing that I have about 1.3TB to use on my server over here - I'm getting so much from the newsgroups I'll be the one supplying my torrent site for a while!

The howto was good - the last script that was upped had an issue with not moving the hellanzb.conf before deleting the directory.

I managed to get it all sorted out and I also have Zussaweb working.
A helpful hint - make sure you change permissions on the daemon.queue directory so you can upload files via the web interface.

---

### Post by zues on 2007-07-13
I got a question, I got everything up and running except my hellanzb folder is locked and it doesnt have daemon queue or usenet folders. So I can't place nzb's into a queue that doesn't exist. Also even if I had the folder's I couldn't drag and drop them into a locked folder. I guess I could use the sudo nautilus command but that seems rediculous.

---

### Post by honeydew on 2007-07-16
man chmod?

sudo chmod -R 777 lockedfolder

---

### Post by Theimon on 2007-07-16
> **zues said:**
> I got a question, I got everything up and running except my hellanzb folder is locked and it doesnt have daemon queue or usenet folders. So I can't place nzb's into a queue that doesn't exist. Also even if I had the folder's I couldn't drag and drop them into a locked folder. I guess I could use the sudo nautilus command but that seems rediculous.

Take ownership of those folders. Open a terminal and do the following:

```
sudo chown -R *your_username*:*your_username* /folder
```Just enter the top folder (I believe it's called /nzb), the -R option recurses so all subfolders are chown-ed too.

Edit: honeydew beat me to the punch, both options give the same result, well....closely......my option only will allow you to wrtie to the folder. Honeydews solution will enable any user to write to the folder.

---

### Post by zues on 2007-07-17
I am having one hell of a time configuring hellanzb. I can get hellanzb running with the command sudo hellanzb.py here is my results:   tommy@tsunami:~$ sudo hellanzb.py
Password:

hellanzb v0.11 (config = /usr/etc/hellanzb.conf)
(/home/tommy/) Opening 4 connections...
hellanzb - Now monitoring queue...




This is good I am pretty sure. Now Im sure the problem lies in the way i configured it here is my sudo gedit /usr/etc/hellanzb.conf.sample






# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 978 2007-01-29 03:00:30Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = '/home/tommy',


             hosts = [ 'unlimited.newshosting.com:119' ],
             #hosts = [ 'unlimited.newshosting.com',
'unlimited.newshosting.com:8000' ],


             username = 'tommyarmour',
             password = 'oxfo',
             #username = tommyarmour,   # no auth
             #password = oxfo,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0             # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb./home/tommy = '/ext2/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb./home/tommy + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb./home/tommy + 'usenet/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb./home/tommy + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb./home/tommy + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb./home/tommy + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb./home/tommy + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb./home/tommy + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
#Hellanzb.PAR2_CMD = None

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = False

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = zues
Hellanzb.NEWZBIN_PASSWORD = oxfo


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'


I do not have  a folder in my /home/tommy/ called nzb it's called hellanzb-0.13 that contains several 2 other folders etc and hellanzb and some info folders. No where is there a daemon.queue folder to put my nzb's or is there a usenet folder to get the downloads once they are complete. Im stumped any help would be awesome thanks.

---

### Post by darqfiber on 2007-07-19
Okay so installed, configured and got hellanzb to run at startup (some small tweaks to the /etc/init.d/hellanzb script to use the binary instead of the .py file)

HellaNZB is accepting input from zussaweb and hellafox and download and par verifying the files, then it stops. 
It doesn't unrar or move the unrar'ed file to the destination directory.

However when I stop and restart hellanzb by logging into a terminal - /etc/init.d/hellanzb stop /etc.init.d/hellanzb start then it suddenly wakes up and unrars and moves files - from then on it seems to function as expected.

Now I suppose I could kludge a /etc/init.d/hellanzb restart into /etc/rc.local and that should get around the issue but why oh why is it doing that - logs and debug logs are clean. Could it be file permissions ? weird.

Any suggestions are very welcome.

Thanks

DF.

---

### Post by chalewa on 2007-07-23
> **darqfiber said:**
> Okay so installed, configured and got hellanzb to run at startup (some small tweaks to the /etc/init.d/hellanzb script to use the binary instead of the .py file)

HellaNZB is accepting input from zussaweb and hellafox and download and par verifying the files, then it stops. 
It doesn't unrar or move the unrar'ed file to the destination directory.

However when I stop and restart hellanzb by logging into a terminal - /etc/init.d/hellanzb stop /etc.init.d/hellanzb start then it suddenly wakes up and unrars and moves files - from then on it seems to function as expected.

Now I suppose I could kludge a /etc/init.d/hellanzb restart into /etc/rc.local and that should get around the issue but why oh why is it doing that - logs and debug logs are clean. Could it be file permissions ? weird.

Any suggestions are very welcome.

Thanks

DF.


mine does the same thing, no unrar action. i have never been able to figure it out

---

### Post by icedfusion on 2007-07-29
> **darqfiber said:**
> Okay so installed, configured and got hellanzb to run at startup (some small tweaks to the /etc/init.d/hellanzb script to use the binary instead of the .py file)

HellaNZB is accepting input from zussaweb and hellafox and download and par verifying the files, then it stops. 
It doesn't unrar or move the unrar'ed file to the destination directory.

However when I stop and restart hellanzb by logging into a terminal - /etc/init.d/hellanzb stop /etc.init.d/hellanzb start then it suddenly wakes up and unrars and moves files - from then on it seems to function as expected.

Now I suppose I could kludge a /etc/init.d/hellanzb restart into /etc/rc.local and that should get around the issue but why oh why is it doing that - logs and debug logs are clean. Could it be file permissions ? weird.

Any suggestions are very welcome.

Thanks

DF.

After using the repository to update my version of hellanzb I had the same problem
I found that the following line does the trick in the config file:

```
Hellanzb.SKIP_UNRAR = False
```

maybe yours is set to true??

I also notice that in the config file has this line:
```
#Hellanzb.UNRAR_CMD = None
```

but as you can see i have it commented out as when i first installed unrar I added it to my path variable.

ice.

---

### Post by icedfusion on 2007-07-29
> **zues said:**
> I am having one hell of a time configuring hellanzb. I can get hellanzb running with the command sudo hellanzb.py here is my results:   tommy@tsunami:~$ sudo hellanzb.py
Password:

hellanzb v0.11 (config = /usr/etc/hellanzb.conf)
(/home/tommy/) Opening 4 connections...
hellanzb - Now monitoring queue...




This is good I am pretty sure. Now Im sure the problem lies in the way i configured it here is my sudo gedit /usr/etc/hellanzb.conf.sample


# Important locations
Hellanzb./home/tommy = '/ext2/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb./home/tommy + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb./home/tommy + 'usenet/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb./home/tommy + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb./home/tommy + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb./home/tommy + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb./home/tommy + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb./home/tommy + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'


From the look of your hellanzb.conf file, it looks like you ahve messed up the directory assignments and confused yourself
When the rars are downloading they should be downloading into your home directory:

```
/home/tommy/.hellanzb
```
(this is a hidden directory so use ctrl+h to list hidden directorys)
You dont really need to see what goes on here, instead you need to sort out where the files are going to be put once they have downloaded.

I would suggest you use this, assuming your home is still as described in your config file, this will store your downloaded files in /home/tommy/downloads/usenet and should scan /home/tommy/downloads for your .nzb files.
```

# Important locations
Hellanzb.PREFIX_DIR = '/home/tommy/downloads/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'usenet/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

```


ice.

---

### Post by phusio on 2007-07-30
Can anyone tell me please how i can make this automatically run at startup on my ubuntu server? I dont know much of scripts.
thanks in advance !

---

### Post by TuxCrafter on 2007-07-31
place your command in you local startup config file 
/etc/rc.local

---

### Post by phusio on 2007-07-31
> **TuxCrafter said:**
> place your command in you local startup config file 
/etc/rc.local

Thank you !!:)

---

### Post by Arumite on 2007-08-06
Please pardon the noob question in advance.

     How do i remove the Hellanzb-0.11 locked folder that is located in my /home/my_username/ directory.

I have tried

```
sudo rm hellanzb-0.11
```

and

```
sudo rm /home/my_username/hellanzb-0.11
```

I get...
rm: cannot remove *blah blah blah": Is a directory

*also how do you copy text from a terminal?

I've have spent WAY too much time to get this working.

I get the problem previously noted in this board where hellanzb is stuck in idle mode.  I loaded the .nzb file into queue and the file gets moved to the current folder automatically, but goes nowhere from there.

Im going to try the Sabnzbd alternative.
Looks like a great piece of software thought.  I would love it if i get it working.
Anyways, any help with the above would be greatly appreciated.

---

### Post by TuxCrafter on 2007-08-07
[QUOTE=Arumite;3145828]

How do i remove the Hellanzb-0.11 locked folder that is located in my /home/my_username/ directory.

*also how do you copy text from a terminal?

to remove a directory recursivly add the -r option
see the man rm manual

```
sudo rm /home/$USER/hellanzb-0.11/ -r
```

To copy text -> select with mouse -> right mouse button -> copy

---

### Post by benchMarc on 2007-08-25
I want to download the files to my own Windows PC, that has a network share. I mounted the share in Ubuntu. The path is smb://192.168.0.50/NewsDownloads/. I've set the path in the hellanzb.conf file to: Hellanzb.PREFIX_DIR = 'smb://192.168.0.50/NewsDownloads/'

But this doesn't work :( I have rights to write on that path. In Nautilus i can make folders etc, so that can't be the problem.

So is it that hellanzb can't work with network paths?

---

### Post by supertux on 2007-08-25
> **benchMarc said:**
> I want to download the files to my own Windows PC, that has a network share. I mounted the share in Ubuntu. The path is smb://192.168.0.50/NewsDownloads/. I've set the path in the hellanzb.conf file to: Hellanzb.PREFIX_DIR = 'smb://192.168.0.50/NewsDownloads/'

But this doesn't work :( I have rights to write on that path. In Nautilus i can make folders etc, so that can't be the problem.

So is it that hellanzb can't work with network paths?

You will have to mount it to a local path like : /mnt/NewsDownloads , then you can specify that in the config file!

---

### Post by benchMarc on 2007-08-25
> **supertux said:**
> You will have to mount it to a local path like : /mnt/NewsDownloads , then you can specify that in the config file!

Yup, found that out 10min after posting :P But tnx anyway :)

---

### Post by darco on 2007-08-25
How do you stop a download? I use alt + c to end the session but when when I restart Hella it restarts the d/l.  Do I delete the .nzb from the daemon-que folder?
thxs
darco

---

### Post by TuxCrafter on 2007-08-26
> **darco said:**
> How do you stop a download? I use alt + c to end the session but when when I restart Hella it restarts the d/l.  Do I delete the .nzb from the daemon-que folder?
thxs
darco

```

	echo "continue command hellanzb.py"
	hellanzb.py continue

	echo "pause command hellanzb.py"
	hellanzb.py pause

	echo "shutdown command hellanzb.py"
	hellanzb.py shutdown
```

Hope this provides enough information (hellanzb.py help)

---

### Post by darco on 2007-08-26
> **TuxCrafter said:**
> ```

	echo "continue command hellanzb.py"
	hellanzb.py continue

	echo "pause command hellanzb.py"
	hellanzb.py pause

	echo "shutdown command hellanzb.py"
	hellanzb.py shutdown
```

Hope this provides enough information (hellanzb.py help)

umm, where do I enter this command, in a different terminal? I tried that and did nothing to the terminal that is d/l  an .nzb...

darco

---

### Post by TuxCrafter on 2007-08-26
> **darco said:**
> umm, where do I enter this command, in a different terminal? I tried that and did nothing to the terminal that is d/l  an .nzb...

darco

just open a terminal window, when you are already downloading with hellanzb. and type ```
 hellanzb.py pause
``` in this new windows and hit the enter button and wait. If it does not work read the help files about hellanzb, I will not be able to help you in that case.

---

### Post by darco on 2007-08-26
> **TuxCrafter said:**
> just open a terminal window, when you are already downloading with hellanzb. and type ```
 hellanzb.py pause
``` in this new windows and hit the enter button and wait. If it does not work read the help files about hellanzb, I will not be able to help you in that case.

Ok, cool...Pause/cancel/shutdown work fine....
thxs!

darco :KS

---

### Post by benchMarc on 2007-08-27
Got another problem now...

HellaNZB downloads my files to my networkdrive on my other pc. But when i use, for example, hellaworld, i can see these error codes:

> ERROR: [ThrottlingProtocol,client] Unhandled ErrorTraceback (most recent call last):  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 48, in callWithLogger    return callWithContext({"system": lp}, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 33, in callWithContext    return context.call({ILogContext: newCtx}, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 59, in callWithContext    return self.currentContext().callWithContext(ctx, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 37, in callWithContext    return func(*args,**kw)---  ---  File "/var/lib/python-support/python2.5/Hellanzb/HellaReactor.py", line 86, in _doReadOrWrite    handleIOError(ioe)  File "/var/lib/python-support/python2.5/Hellanzb/HellaReactor.py", line 70, in _doReadOrWrite    why = getattr(selectable, method)()  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 362, in doRead    return self.protocol.dataReceived(data)  File "/usr/lib/python2.5/site-packages/twisted/protocols/policies.py", line 132, in dataReceived    ProtocolWrapper.dataReceived(self, data)  File "/usr/lib/python2.5/site-packages/twisted/protocols/policies.py", line 72, in dataReceived    self.wrappedProtocol.dataReceived(data)  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/Protocol.py", line 772, in dataReceived    return self.dataReceivedToFile(data)  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/Protocol.py", line 868, in dataReceivedToFile    self.write(data)exceptions.IOError: [Errno 5] Input/output error
ERROR: [ThrottlingProtocol,client] Unhandled ErrorTraceback (most recent call last):  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 48, in callWithLogger    return callWithContext({"system": lp}, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 33, in callWithContext    return context.call({ILogContext: newCtx}, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 59, in callWithContext    return self.currentContext().callWithContext(ctx, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 37, in callWithContext    return func(*args,**kw)---  ---  File "/var/lib/python-support/python2.5/Hellanzb/HellaReactor.py", line 86, in _doReadOrWrite    handleIOError(ioe)  File "/var/lib/python-support/python2.5/Hellanzb/HellaReactor.py", line 70, in _doReadOrWrite    why = getattr(selectable, method)()  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 362, in doRead    return self.protocol.dataReceived(data)  File "/usr/lib/python2.5/site-packages/twisted/protocols/policies.py", line 132, in dataReceived    ProtocolWrapper.dataReceived(self, data)  File "/usr/lib/python2.5/site-packages/twisted/protocols/policies.py", line 72, in dataReceived    self.wrappedProtocol.dataReceived(data)  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/Protocol.py", line 772, in dataReceived    return self.dataReceivedToFile(data)  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/Protocol.py", line 868, in dataReceivedToFile    self.write(data)exceptions.IOError: [Errno 5] Input/output error
ERROR: [ThrottlingProtocol,client] Unhandled ErrorTraceback (most recent call last):  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 48, in callWithLogger    return callWithContext({"system": lp}, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 33, in callWithContext    return context.call({ILogContext: newCtx}, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 59, in callWithContext    return self.currentContext().callWithContext(ctx, func, *args, **kw)  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 37, in callWithContext    return func(*args,**kw)---  ---  File "/var/lib/python-support/python2.5/Hellanzb/HellaReactor.py", line 86, in _doReadOrWrite    handleIOError(ioe)  File "/var/lib/python-support/python2.5/Hellanzb/HellaReactor.py", line 70, in _doReadOrWrite    why = getattr(selectable, method)()  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 362, in doRead    return self.protocol.dataReceived(data)  File "/usr/lib/python2.5/site-packages/twisted/protocols/policies.py", line 132, in dataReceived    ProtocolWrapper.dataReceived(self, data)  File "/usr/lib/python2.5/site-packages/twisted/protocols/policies.py", line 72, in dataReceived    self.wrappedProtocol.dataReceived(data)  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/Protocol.py", line 772, in dataReceived    return self.dataReceivedToFile(data)  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/Protocol.py", line 868, in dataReceivedToFile    self.write(data)exceptions.IOError: [Errno 5] Input/output error

Wouldn't be a problem if it would all work, but it doesn't. After downloading it doesn't par or extract. And looking at those errors, he got probems with parring while downloading, i guess.

What can this be?

---

### Post by terry_gardener on 2007-08-27
this is a great idea tried the how to steps but when i do step 9 running the hellanzb.py i get error 

terry@terry-desktop:~/Downloads/hellanzb-0.9$ hellanzb.py
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

can some one tell me what is wrong and how to fix it. 

thanks

---

### Post by benchMarc on 2007-09-02
Someone's got a sollution to my last post? Could it be there's a problem with HellaNZB parring/extracting and network shares?

---

### Post by benchMarc on 2007-09-14
No one knows?

---

### Post by GoatTuber on 2007-09-17
> **terry_gardener said:**
> this is a great idea tried the how to steps but when i do step 9 running the hellanzb.py i get error 

terry@terry-desktop:~/Downloads/hellanzb-0.9$ hellanzb.py
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

can some one tell me what is wrong and how to fix it. 

thanks

it looks like it's having trouble importing from the twisted module. Make sure you have python-twisted installed from Synaptic, or from a terminal run:
sudo apt-get install python-twisted

---

### Post by GoatTuber on 2007-09-17
> **benchMarc said:**
> Got another problem now...

HellaNZB downloads my files to my networkdrive on my other pc. But when i use, for example, hellaworld, i can see these error codes:

Wouldn't be a problem if it would all work, but it doesn't. After downloading it doesn't par or extract. And looking at those errors, he got probems with parring while downloading, i guess.

What can this be?


Sorry, I've never tried using hellanzb with a shared drive. Do you get that same error if all the files are processed from a local drive? If it works that way, you might be able to get away with it if you add the share into your fstab so you see it like a local drive. There's a good tip how to do that here: [https://answers.launchpad.net/ubuntu/+question/6644](https://answers.launchpad.net/ubuntu/+question/6644)

---

### Post by Kirobhan on 2007-09-18
You need to install the newest version of Hellanzb.  As of this post it is "hellanzb-0.13.tar.gz".  You can download the newest version from this address: 
[http://www.hellanzb.com/distfiles/]("http://www.hellanzb.com/distfiles/")

I had the same problem.  I assume because the python-twisted installed from the repositories is a newer version which is causing the the older Hellanzb script to fail.

-Kia

---

### Post by benchMarc on 2007-09-28
> **GoatTuber said:**
> Sorry, I've never tried using hellanzb with a shared drive. Do you get that same error if all the files are processed from a local drive? If it works that way, you might be able to get away with it if you add the share into your fstab so you see it like a local drive. There's a good tip how to do that here: [https://answers.launchpad.net/ubuntu/+question/6644](https://answers.launchpad.net/ubuntu/+question/6644)

Thanks for your post. I tried it and i managed to map my share as a local drive. But there's one problem. I can't upload a nzb file from Zussaweb. It complains about chmod rights. As root i can add and delete files to the share, i can also do that as a normal user. But when i try uploading a file via Zussaweb (that runs on my apache server) it doesn't work. I can't chmod or chgrp anything. When i do this via the GUI it just changes back to the old setting. It's strange, because it says at permission for others: read and write.

:-k

---

### Post by Hopworks on 2007-10-05
I hate asking for help on this, but I've read through this thread, and a few others, and I'm missing something big time I'm sure. Sorry for the long post. I wanted to include as much detail as possible minus the conf file, etc.

I'm using Ubuntu Feisty 7.04 with Gnome and I have been using hellanzb for quite awhile, successfully for the most part. What I can't seem to get my head around is the xml-rpc features. To start it, I have been either opening a terminal window or I use putty from my windows xp laptop. I use the command hellanzb.py to start it, and it waits, telling me it is monitoring the queue. When I get an nzb file, I put it in the queue folder I have set for new nzb files. Everything works fine from there, the file disappears, the downloading starts, when it is done, the archive is par checked and processed, and placed in my usenet folder. Like I said before, this whole process works fine for me. There are no lockups, exception errors, and for the most part the end result in my usenet folder is exactly what I want.

But when I want to stop using hellanzb, I have to kill the process in the system monitor. Everything I tried other than that gives me an error
```
hellanzb v0.12 (config = /usr/etc/hellanzb.conf)
Couldn't listen on any:8760: (98, 'Address already in use').
Exiting: FatalError'>: Cannot bind to XML RPC port, is another hellanzb queue daemon already running?

```
Do I have something configured wrong?
Also, I tried accessing hellanzb using the address in the conf file, using firefox on my windows machine, changing the address appropriately (not shown here) as stated, like [http://hellanzb:myusername@mydomain:8760](http://hellanzb:myusername@mydomain:8760)
and I get a pop up dialog asking for username and password. I tried it with a password, without a password, the password in the conf file, the user's actual password in ubuntu, and the dialog just reappears after I click OK. If I cancel, I get ACCESS DENIED.

Sorry for the long winded cry for help. I've googled this XML-RPC thing for months with no success.

EDIT: It's magic. Almost every time I give up and post for some help, a solution comes around. I tried out Zussaweb and everything I wanted to do is possible now. The code is a great tutorial to study too, if you're into PHP. I made some changes for myself to show free space on the two drives as a percentage and in gigs, added a few other things I wanted, but it's really neat how you can talk to hellanzb using the XMLRPC server. >hop<

---

### Post by Octagonal on 2007-10-07
Great post, thank you for the information.
Works like a dream.

---

### Post by cchester on 2007-10-08
> **Hopworks said:**
> I tried out Zussaweb and everything I wanted to do is possible now. The code is a great tutorial to study too, if you're into PHP. I made some changes for myself to show free space on the two drives as a percentage and in gigs, added a few other things I wanted, but it's really neat how you can talk to hellanzb using the XMLRPC server. >hop<

Hi,

Could you give me a step by step on how you installed Zussaweb. I have tried everything with zero luck in getting it to run I guess I just don't get how to make it work. I have Hellanzb working I just need something like Zissaweb to be completely happy.

Thanks for any help.

---

### Post by GoatTuber on 2007-10-11
> **benchMarc said:**
> Thanks for your post. I tried it and i managed to map my share as a local drive. But there's one problem. I can't upload a nzb file from Zussaweb. It complains about chmod rights. As root i can add and delete files to the share, i can also do that as a normal user. But when i try uploading a file via Zussaweb (that runs on my apache server) it doesn't work. I can't chmod or chgrp anything. When i do this via the GUI it just changes back to the old setting. It's strange, because it says at permission for others: read and write.

:-k

If you have read/write access to the directory the nzb files are going to, but not on the nzb files themselves when they're received, you might be able to get it working by setting the default permissions with a umask. See [http://www.linuxsecurity.com/content/view/117255/161/](http://www.linuxsecurity.com/content/view/117255/161/) for more info.

---

### Post by GoatTuber on 2007-10-11
> **Hopworks said:**
> But when I want to stop using hellanzb, I have to kill the process in the system monitor. Everything I tried other than that gives me an error
```
hellanzb v0.12 (config = /usr/etc/hellanzb.conf)
Couldn't listen on any:8760: (98, 'Address already in use').
Exiting: FatalError'>: Cannot bind to XML RPC port, is another hellanzb queue daemon already running?

```


Do you get that error message if you run "hellanzb shutdown" in a terminal window? What else have you tried?

---

### Post by cchester on 2007-10-11
I get no errors when shutting down.

I fixed it by placing the folder i extracted zussaweb to /var/www/ and then everything was ok.

The only error I have now is it says line 4 error disk space.

Thanks for the reply and if anyone knows how to fix the above error let me know please. It isn't making it not download but I would like to be error free.

Thanks again.

---

### Post by dasbooter on 2007-10-15
> **robertpolson said:**
> Can you please elaborate on this as when I enter screen -S hellanzb -d -m hellanzb   into the terminal, nothing happens.

Also, with the version from repositories, the older one there is no SSL encryption and this sucks.


Uhmm yes I would also like to know what the advantage of running this with screen -S is. 
I have done a man screen but I cant figure it out. Also option -m I dont see it with man hellanzb (0.10)
Also I am wondering, can we just run a little startup script in gnome sessions. I am not in a situation where multiple users use the daemon. It would be nice to have some graphical feedback besides the console just for download progress, is there something simple that exists I dont use conqe but do use gkrellm. Just throwing that last question out there. By the way all seems to be running nicely here with the version from the repos. Par and rar running fine so far.The files are being downloaded to a local folder located on a raid.

---

### Post by Hopworks on 2007-10-16
> **cchester said:**
> I get no errors when shutting down.

I fixed it by placing the folder i extracted zussaweb to /var/www/ and then everything was ok.

The only error I have now is it says line 4 error disk space.

Thanks for the reply and if anyone knows how to fix the above error let me know please. It isn't making it not download but I would like to be error free.

Thanks again.
What php file throws the error? I completely rewrote the disk space reporting in my copy.
Sorry I didn't answer you about accessing the web gui before, I just read your question. It seems you figured it out though, nice work. =)

---

### Post by Dedors on 2007-10-16
Updated init script

now supports starting of hellahella
layout was done according to other init scripts

```
#! /bin/bash
#
### BEGIN INIT INFO
# Provides:		hellanzb, hellahella
# Required-Start:	$network $local_fs
# Required-Stop:
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short-Description:	Usenet Binary Downloader
### END INIT INFO
#
# hellanzb       Start the hellanzb and hellahella
#
# hellanzb init-script v0.6 dedicated
# 
# the following vars are used:
# NAME= leave it to hellanzb, its just a display name and it is used to connect to it with screen
# USERNAME= your username, this is used to run hellanzb in
# *_PIDFILE= the pid file which the script checks
# WEBIF_ENABLED if you are running hellahella and want this to start with hellanzb
#



NAME=hellanzb
NAMEWEB=hellahella
USERNAME=dedi
HELLANZB_PIDFILE=/var/run/hellanzb.pid
HELLAHELLA_PIDFILE=/var/run/hellahella.pid
WEBIF_ENABLED=1
HELLANZB_BIN=/usr/bin/hellanzb
HELLAHELLA_INI=/opt/hellahella/hella.ini
DESC="Binary Usenet Download Services:"

trap "" 1
export LANG=C

. /lib/lsb/init-functions

case "$1" in
  start)
    log_action_msg "Starting $DESC"

    log_daemon_msg "   Starting $NAME.."
    if start-stop-daemon -S -c $USERNAME -m -b --pidfile $HELLANZB_PIDFILE --exec /usr/bin/screen -- -S $NAME -D -m $HELLANZB_BIN; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	if test "$WEBIF_ENABLED" != "0"; then
            log_daemon_msg "   Starting $NAMEWEB.."
	    if start-stop-daemon -S -c $USERNAME -m -b --pidfile $HELLAHELLA_PIDFILE --exec /usr/bin/screen -- -S $NAMEWEB -D -m paster serve $HELLAHELLA_INI; then
	    	log_end_msg 0
	    else
		log_end_msg 1
	    fi
	fi
    ;;

  stop)
    log_action_msg "Stopping $DESC"
    log_daemon_msg "   Stopping $NAME.."
        if start-stop-daemon -K --pidfile $HELLANZB_PIDFILE; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	if test "$WEBIF_ENABLED" != "0"; then
    	    log_daemon_msg "   Stopping $NAMEWEB.."
	    if start-stop-daemon -K --pidfile $HELLAHELLA_PIDFILE; then
	    	log_end_msg 0
	    else
		log_end_msg 1
	    fi
	fi
    ;;

  restart)
    $0 stop
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/$NAME start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

remember:
```
ln -s /etc/init.d/hellanzb /etc/rc2.d/S20hellanzb
ln -s /etc/init.d/hellanzb /etc/rc3.d/S20hellanzb
ln -s /etc/init.d/hellanzb /etc/rc4.d/S20hellanzb
ln -s /etc/init.d/hellanzb /etc/rc5.d/S20hellanzb
```

```
screen -R hellanzb
```

leave it with

```
ctrl-a d
```

---

### Post by TuxCrafter on 2007-10-22
So took me a while to fix some issues, but here it is: **The Gusty Gibbon Hellanzb NZB downloader installation script**. Please let me know if you got any feedback. :KS

---

### Post by frolle on 2007-10-23
Its very strange. When i am downloading with hellanzb its lagging. It seems like sometimes its eating my cpu. Does anyone have the same problem?

---

### Post by cchester on 2007-10-23
> **TuxCrafter said:**
> So took me a while to fix some issues, but here it is: **The Gusty Gibbon Hellanzb NZB downloader installation script**. Please let me know if you got any feedback. :KS

Ok a couple of questiions:

On option 3 I put in the info but I can't find a way to save it and exit the screen. How do I do that.

Then on option 4 I chose to install hellanzb again. (why are we needing to do this first since we do it in option 1 from the repositories?)

Then on option 5 remove hellanzb from the system I did this. Also are you having the user do this because we installed it again in option 4 and we are now removing the one that installed from the repositories?

I am a little confused. So do we need to do just 1 - 3 and we are done and can run hellanzb or is option 4 for those who don't want to install it from the repositories only.

Just need a little clarifying. I installed this in Ubuntu 7.10 by the way and didn't notice any errors during the install process.

A note : just tried to run if after doing all the options and it came back and said it isn't installed and I can install it from the repositories.

Thanks for any help on this script that you created it is great.:)

---

### Post by TuxCrafter on 2007-10-23
> **cchester said:**
> Ok a couple of questiions:

On option 3 I put in the info but I can't find a way to save it and exit the screen. How do I do that.

Then on option 4 I chose to install hellanzb again. (why are we needing to do this first since we do it in option 1 from the repositories?)

Then on option 5 remove hellanzb from the system I did this. Also are you having the user do this because we installed it again in option 4 and we are now removing the one that installed from the repositories?

I am a little confused. So do we need to do just 1 - 3 and we are done and can run hellanzb or is option 4 for those who don't want to install it from the repositories only.

Just need a little clarifying. I installed this in Ubuntu 7.10 by the way and didn't notice any errors during the install process.

A note : just tried to run if after doing all the options and it came back and said it isn't installed and I can install it from the repositories.

Thanks for any help on this script that you created it is great.:)

So a lot of questions:

First: The recommended install is to do step 1 to 3

Second: The script uses the default installed vim editor to edit the personal configuration file. If you don't know how to use vim. You can search the script for "vim" and replace it with an other editor like "gedit".

Third: Option 4 and 5 are for manually compiled versions of hellanzb. This way you can be sure you have the latest version. Note that the personal configuration does not work the same with these options.

Maybe if you change the editor to gedit and re run the script with option 1 -> 2 -> 3. It will work fine.

Thanks for the feedback, hope to here form you soon.

---

### Post by cchester on 2007-10-23
Thanks for the reply. I couldn't find the place in the script to change it to gedit. I saw the word vim and changed that to gedit but that didn't work.

So if you could point me in the right direction that would be great.:)

Ok so kill me it was more than a couple of questions. Just started to think of more as I typed.

Also I get no write access error for the ./hellanzb directory if you could help me on that too.

Thanks again.

---

### Post by marklid on 2007-10-23
> **TuxCrafter said:**
> So took me a while to fix some issues, but here it is: **The Gusty Gibbon Hellanzb NZB downloader installation script**. Please let me know if you got any feedback. :KS

Worked an absolute treat !! Cheers pal !

---

### Post by cwhisperer on 2007-10-23
the last dist file on [http://www.hellanzb.com/distfiles/](http://www.hellanzb.com/distfiles/) 0.13 works like expected on ubuntu 7.10 ;)

---

### Post by TuxCrafter on 2007-10-23
At special request cchester a new version for the hellanzb script with automatic GUI file editor detection and enhanced hellanzb removal. 

[B]The Gusty Gibbon Hellanzb NZB downloader installation script
version: 0.0.8 
date: 23-10-07
[/B]
If you encounter permission problems due to previous attempt to install hellanzb. Run the script with option 5 and you should have a clean machine to reinstall hellanzb.

Feedback is again welcome.

---

### Post by cchester on 2007-10-24
> **TuxCrafter said:**
> At special request cchester a new version for the hellanzb script with automatic GUI file editor detection and enhanced hellanzb removal. 

[B]The Gusty Gibbon Hellanzb NZB downloader installation script
version: 0.0.8 
date: 23-10-07
[/B]
If you encounter permission problems due to previous attempt to install hellanzb. Run the script with option 5 and you should have a clean machine to reinstall hellanzb.

Feedback is again welcome.

Thanks so much you are the best. Still had a permission problem even after uninstalling and reinstalling. Hellanzb complained and said I didn't have permission but I fixed that. Great script.

Think you could please get the one to install SABnzbd-0.2.4 correctly working as well that way people can have a GUI for Hellanzb to go along with it or is that asking too much.:)

I ask because the one that is there seems to have problems with Ubuntu 7.10 when you get to this part:

tar -xzvf CherryPy-2.2.1.tar.gz
cd CherryPy-2.2.1
/usr/local/sabnzbd/bin/python setup.py install

I think I recall it saying something like invalid command cannot run or something like that.

If not you are great still and I thank you.:)

---

### Post by TuxCrafter on 2007-10-24
> **cchester said:**
> Think you could please get the one to install SABnzbd-0.2.4 correctly working as well that way people can have a GUI for Hellanzb to go along with it or is that asking too much.:).

I peronaly don't have a need for SABnzbd, i think its a bid ugly. I do have request and ideas to make a script for Zussaweb. However this tools needs a complete apache configuration to work. [http://sourceforge.net/projects/zussaweb](http://sourceforge.net/projects/zussaweb)

Currently I use 4 separated scripts to integrate hellanzb in my complete desktop environment. I can right click on a nzb file and choice to start downloading. Then I have script to control the rest like par2 unrar pyton pause continue shutdown etcetera. I also have script that give me automatic configuration options so I can easily change the the download location to a usb harddisk. GUI or webpage isn't really necessary. But for remote control of hellanzb it will be great.

---

### Post by frolle on 2007-10-24
Anyone having problems when you reset the max speed for download? When i do that it just tops completly. Any ideas?

---

### Post by cchester on 2007-10-24
> **TuxCrafter said:**
> .

I peronaly don't have a need for SABnzbd, i think its a bid ugly. I do have request and ideas to make a script for Zussaweb. However this tools needs a complete apache configuration to work. [http://sourceforge.net/projects/zussaweb](http://sourceforge.net/projects/zussaweb)

Currently I use 4 separated scripts to integrate hellanzb in my complete desktop environment. I can right click on a nzb file and choice to start downloading. Then I have script to control the rest like par2 unrar pyton pause continue shutdown etcetera. I also have script that give me automatic configuration options so I can easily change the the download location to a usb harddisk. GUI or webpage isn't really necessary. But for remote control of hellanzb it will be great.

Yeah I don't mind the command line for Hellanzb that much either. Would love to have those 4 scripts that you use would pretty much end my need or want for a Gui.

I forgot about Zussawed that would be great too.

Thanks for the reply.

---

### Post by Malik on 2007-10-24
How do you restar hella? its stuck on queue mode :(

---

### Post by frolle on 2007-10-25
You just open and close it - if you want to restart hellanzb.

---

### Post by vangos on 2007-10-25
First, many thanks for all your work. From the first looks it seems that it works fine..

I have two questions:

1. How do you remove a .NZB file out of the queue so it is not considered any more for download? Is it it enough to physically remove it from the folder?

2. During my initial attempt to install the program I used the instructions in the beginning of the thread. Then by reading on I realized that not only the program is now at 0.13 version, but there is a script that does everything for you. When I tried to uninstall the 0.9 version that I had manually installed, with the assistance of the script, I saw that it did not uninstall it. I went ahead and used the script 3 times as recommended, fixed the .config file, and now it looks that everything is working fine ( I am downloading away as we speak). Is there any way I can safely remove the old version? I am afraid I will mess up the current installation.

Thanks

Vangelis

---

### Post by TuxCrafter on 2007-10-26
> **vangos said:**
> First, many thanks for all your work. From the first looks it seems that it works fine..

I have two questions:

1. How do you remove a .NZB file out of the queue so it is not considered any more for download? Is it it enough to physically remove it from the folder?

2. During my initial attempt to install the program I used the instructions in the beginning of the thread. Then by reading on I realized that not only the program is now at 0.13 version, but there is a script that does everything for you. When I tried to uninstall the 0.9 version that I had manually installed, with the assistance of the script, I saw that it did not uninstall it. I went ahead and used the script 3 times as recommended, fixed the .config file, and now it looks that everything is working fine ( I am downloading away as we speak). Is there any way I can safely remove the old version? I am afraid I will mess up the current installation.

Thanks

Vangelis


1.  see hellanzb --help

hellanzb clear
Clear the current nzb queue. Specify True as the second argument to clear anything currently downloading as well (like the cancel call)

hellanzb dequeue nzbid
Remove the NZB with specified ID from the queue

2. Do not try to remove it it will mess up your current working system.

---

### Post by TuxCrafter on 2007-10-26
I created a new topic so i can provide better support in the further with hellanzb. As told earlier i got a bunch of script to integrate hallanzb into the desktop environment and I am working up to a release of this system.

HOW TO: Installation of hellanzb NZB usenet downloader
[http://ubuntuforums.org/showthread.php?t=589618](http://ubuntuforums.org/showthread.php?t=589618)

-- -- --

HOW TO: Compiling and Installing the OpenChrome Graphical VIA Driver
[http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

HOW TO: Installation of the SCR335 smartcard reader
[http://ubuntuforums.org/showthread.php?t=589625](http://ubuntuforums.org/showthread.php?t=589625)

HOW TO: Installation of lib-xine based multimedia codecs
[http://ubuntuforums.org/showthread.php?t=589655](http://ubuntuforums.org/showthread.php?t=589655)

HOW TO: Installation of a complete vmware server setup
[http://ubuntuforums.org/showthread.php?t=589638](http://ubuntuforums.org/showthread.php?t=589638)

HOW TO: Setting up xfce xft font rendering settings
[http://ubuntuforums.org/showthread.php?t=589593](http://ubuntuforums.org/showthread.php?t=589593)

HOW TO: Setting up xorg LCD 96 DPI native monitor settings
[http://ubuntuforums.org/showthread.php?t=589574](http://ubuntuforums.org/showthread.php?t=589574)

---

### Post by Mithrilhall on 2007-10-26
Anyone know of a Superkaramba theme that displays hellanzb info like; files in queue, currently downloading, etc. or should I start writing one?

---

### Post by TuxCrafter on 2007-10-26
> **Mithrilhall said:**
> Anyone know of a Superkaramba theme that displays hellanzb info like; files in queue, currently downloading, etc. or should I start writing one?

Nope not that i know of ...

---

### Post by vangos on 2007-10-27
Thanks TuxCrafter for the help. I did not realize that there is so much built-in help in the program.

I will most definitely not touch the other version installation.

Vangos

---

### Post by goonies on 2007-10-27
```
Found new nzb: whatiwantedtodownload - Season 1 [DVD 1_5]
[-] Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/usr/lib/python2.5/site-packages/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/Hellanzb/NZBQueue.py", line 204, in scanQueueDir
    move(nzbfile, Hellanzb.CURRENT_DIR)
  File "shutil.py", line 199, in move
    copy2(src,dst)
  File "shutil.py", line 92, in copy2
    copystat(src, dst)
  File "shutil.py", line 67, in copystat
    os.utime(dst, (st.st_atime, st.st_mtime))
exceptions.OSError: [Errno 1] Operation not permitted: '/media/library/usenet/nzb/daemon.current/whatiwantedtodownload - Season 1 [DVD 1_5].nzb'
```

Can someone tell me whats going on here?  It eventually works when I close out hellanzb and restart it.  But then when it is time for hellanzb to move the processed files over to my complete folder it gives a similar error and tries to redownload the already done nzb.  What gives?

---

### Post by TuxCrafter on 2007-10-27
> Can someone tell me whats going on here? It eventually works when I close out hellanzb and restart it. But then when it is time for hellanzb to move the processed files over to my complete folder it gives a similar error and tries to redownload the already done nzb. What gives?

Maybe rename the original nzb file to a very simple save name like simple.nzb and download things again. Maybe it works please let us know.

---

### Post by goonies on 2007-10-28
```
Found new nzb: wire
[-] Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/usr/lib/python2.5/site-packages/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/Hellanzb/NZBQueue.py", line 204, in scanQueueDir
    move(nzbfile, Hellanzb.CURRENT_DIR)
  File "shutil.py", line 199, in move
    copy2(src,dst)
  File "shutil.py", line 92, in copy2
    copystat(src, dst)
  File "shutil.py", line 67, in copystat
    os.utime(dst, (st.st_atime, st.st_mtime))
exceptions.OSError: [Errno 1] Operation not permitted: '/media/library/usenet/nzb/daemon.current/wire.nzb'
```

Again =\  I've never had this problem before on Feisty with the same version of hellanzb.

---

### Post by mangurt on 2007-10-28
wow, does my brain ever hurt....

Ok, I have been trying to follow this thread to get hellanbz.  I think I followed the stuff on the first page and can only get to step 4 (unpack hellanbz) when I get this error

tar: hellanzb-0.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I am rather new at the whole linux thing, and love, love, LOVE newsgroups, and would love to get this going....

I saw on the last page that there was a shell post, and I downloaded that, but have no clue on what to do with it, how to open it, ect...and when I went to the page, it said that it was moved...so I am not lost with that.

Thanks for the help

---

### Post by TuxCrafter on 2007-10-29
```
Operation not permitted
```

Are you sure you have correct permissions on all files and locations?

---

### Post by TuxCrafter on 2007-10-29
> **mangurt said:**
> wow, does my brain ever hurt....

Thanks for the help

>>> [http://tinyurl.com/ywvtcw](http://tinyurl.com/ywvtcw)

---

### Post by dasbooter on 2007-10-29
Is anybody out there using hellanzb with a rss reader to automatically filter and download certain nzb's into the download queue folder? I have had a couple of runs at it and so far no luck. With hellas already excellent automation it only seems like the most likely next step. Thanks for reading ... interested to hear your solutions

---

### Post by TuxCrafter on 2007-10-29
> **dasbooter said:**
> Is anybody out there using hellanzb with a rss reader to automatically filter and download certain nzb's into the download queue folder? I have had a couple of runs at it and so far no luck. With hellas already excellent automation it only seems like the most likely next step. Thanks for reading ... interested to hear your solutions

hmm never tried it, also no personal need to do so on this moment. looks interesting though.

---

### Post by dasbooter on 2007-10-30
> **TuxCrafter said:**
> hmm never tried it, also no personal need to do so on this moment. looks interesting though.

Here is my scenario. RSS akregator watches feed according to filter I have set and downloads nzb files of a high defintion show I like to watch to the Hellanzb queue folder.Hellanzb does the rest and puts the finished product in a folder that I share out for my xbox 360. Bing turn on the xbox 360 and the TV and episode almost magically appears to watch thanks to Hellanzb. 

 Hella Yeah :guitar:

---

### Post by mangurt on 2007-10-31
Ok, my head is still hurting....I feel like I am so clueless right now...

I followed the link to get the hellanbz.sh file, but I still don't know what to do with it.  Any help would be greatly appreciated.
Thanks

---

### Post by goonies on 2007-11-03
> **goonies said:**
> ```
Found new nzb: wire
[-] Unhandled Error
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/usr/lib/python2.5/site-packages/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/Hellanzb/NZBQueue.py", line 204, in scanQueueDir
    move(nzbfile, Hellanzb.CURRENT_DIR)
  File "shutil.py", line 199, in move
    copy2(src,dst)
  File "shutil.py", line 92, in copy2
    copystat(src, dst)
  File "shutil.py", line 67, in copystat
    os.utime(dst, (st.st_atime, st.st_mtime))
exceptions.OSError: [Errno 1] Operation not permitted: '/media/library/usenet/nzb/daemon.current/wire.nzb'
```

Again =\  I've never had this problem before on Feisty with the same version of hellanzb.

Anyone?

---

### Post by chalewa on 2007-11-04
still have never been able to get this thing to unrar what it downloads. i love the program, but the unrar feature would really solidify it for me. 


any ideas on what i could be missing?

---

### Post by Mithrilhall on 2007-11-05
Download rar and par2 via adept or apt-get and make sure your hellanzb.conf file looks like so...

> 
# Disable SMART_PAR (download all PAR files)
Hellanzb.SMART_PAR = True

# Supply a path to the (un)rar command
Hellanzb.UNRAR_CMD = '/usr/bin/rar'

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = False


P.S.

Can someone tell me what I need to get libnotify working? I had it working in the past and I can't remember what files I needed to get it working (besides libnotify and python-notify).

---

### Post by benfindlay on 2007-11-16
Hey guys, not sure if this precise error has been posted somewhere else in this thread, as there are quite a lot of very similar errors. Anyway, I'm trying to get hellanzb to work on my friend's 7.10 server (it works fine on my 6.06 server). I keep getting the following error when I launch it:

> user1@server:~$ hellanzb.py 
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize
user1@server:~$ 


Has anyone had this error, or can anyone suggest a way to fix it?

Cheers
Ben

---

### Post by kd7swh on 2007-11-16
Ben,

I had a similar problem on one of my boxes. I made a set of folders and changed the config file, and it works like a charm again. I don't know why.

Best of Luck,

Jon

---

### Post by downhillgames on 2007-11-17
I'm not going to read 25 pages to say this...

I just use nzb, pypar2 and 7zip... apt-get install nzb pypar2 p7zip

just like grabit, quickpar and 7zip in windows. (cept it doesn't auto-unrar, but that's ok. I'm not _That_ lazy ;))

---

### Post by kd7swh on 2007-11-17
this howto is really out of date anyway. hellanzb in in the repos. now. I should write a New HowTo: and include a webUI and C Yenc, but I don't have time right now. Maybe for Christmas.

---

### Post by Hopworks on 2007-11-19
I'm here at my laptop this morning, learning how to write a webUI for Hellanzb using XML-RPC, and I figured out how to get a list of methods, descriptions, and signatures from hellanzb on my Feisty server. I'm using hellanzb version 0.12

I'm going through that list and there is one weird method listed called aolsay.

[COLOR="Sienna"]*[FONT="Trebuchet MS"]snippet from a list of all the methods generated by a simple test.php page on my server[/FONT]*[/COLOR]...```
[system.methodList] aolsay
[system.methodHelp] Return a random aolsay (from Da5id's aolsay.scr)
[system.methodSignature] [string]
```

I gotta ask, what in the world is the point of that method? I'd post a couple of text lines it returns, but I'd probably get banned. It's some of the nastiest script-kiddy I ever read. :rolleyes:
 
Check it out. What is it anyway? An Easter Egg? :D

It doesn't matter to me really, just curious. I love hellanzb. I can't remember the last time I looked at a windows based NNTP client. Thank you!

---

### Post by joecrappa on 2007-11-21
Hi all, new to the ubuntu forums.

Just installed Gutsy last night and I'm trying to get hellanzb working. I've downloaded the hellanzb.ph installer and ran it to try and fix my issue to no avail. Here is my error:

> hellanzb v0.13 (config = /usr/etc/hellanzb.conf, C yenc module)
Couldn't listen on any:8760: (98, 'Address already in use').
Exiting: FatalError'>: Cannot bind to XML RPC port, is another hellanzb queue daemon already running?


I get this error when I "sudo hellanzb.py"

it created the folders but will not run, I hope someone can give me an answer,

Thanks in advance

---

### Post by Hopworks on 2007-11-21
It's probably out there a little, and not your problem's solution, but I always get that error, the last part anyway when hellanzb is already running. Did you look at your processes to see if it is running already?
***System/Administration/System Monitor (Processes tab)***

Hop

P.S. Welcome to the forums and the community! I hope you find them as incredibly helpful as I have so far. :D

---

### Post by mikebeecham on 2007-11-21
hi there...

I have followed the instructions to the letter, but when I enter hellanzb.py, I get this:

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize


Help?

---

### Post by benfindlay on 2007-11-22
> **mikebeecham said:**
> hi there...

I have followed the instructions to the letter, but when I enter hellanzb.py, I get this:

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize


Help?

Hi Mike, I get the exact same error, and there seems to be no solution known for it. Your best bet is to use nzb, pypar2 and p7zip which you can install with 

```
apt-get install nzb pypar2 p7zip
```

nzb uses a gui as opposed to the terminal

Hope this helps!

---

### Post by TuxCrafter on 2007-11-22
please use the script in the hellanzb topic that can be found in my signature, this should work fine. If you have hellanzb installed remove it first. (this can be done with the script)

---

### Post by mikebeecham on 2007-11-22
sorry guys, could I get real basic support on this?  I've been using Linux less than a week and it's fair to say that most of it is confusing me.

If I need to uninstall hellanzb then how would I do this?

Where do i go from there?

Thanks

---

### Post by benfindlay on 2007-11-22
To get rid of hellanzb just type ```
sudo apt-get remove hellanzb
``` into the terminal.

Hope this helps

---

### Post by Timsy321 on 2007-11-22
Can anyone help me out here. I just donwloaded a season of Family guy with hellanzb and then it placed it in my finished folder. But now i have to go through and click like every three rar files to get one episode. Is there any way i can just select them on and then extract them all at once? i tried ctrl-a and it just opened about 40 boxes.

---

### Post by Hopworks on 2007-11-22
> **Timsy321 said:**
> Can anyone help me out here. I just donwloaded a season of Family guy with hellanzb and then it placed it in my finished folder. But now i have to go through and click like every three rar files to get one episode. Is there any way i can just select them on and then extract them all at once? i tried ctrl-a and it just opened about 40 boxes.

I never used the install script, and still using version 0.12, but I followed a lot of posts and set it up to get the archive, par check it, then unrar it. About 99% of the time, unless the archive is too full of holes, after the whole process is over with, I have the extracted archive in its own folder in the folder I specified in the config file. I rarely need to worry about manually unrar'ing the archive, etc.

I'll try to find those posts I used as a guide, and I'm sure the author has improved hellanzb with his install script. I just worked through a harder way a few months ago, and the application works great for me on my Feisty Server 7.04.

It's Thanksgiving so I don't have much time atm, but I'll try to post what I did to get it working.

Also, I never could figure out how to control Hellanzb via the command line. I kept getting errors about how the port was busy and is there another instance already running. I then discovered Zussaweb, modified it, played with the XML-RPC engine, and I'm happy with the control I have now. It's good to note that I have my Feisty configured as a LAMP server, so using web interfaces is pretty easy for my clients.

Also good to note too is that when I group a few archives in an nzb file, if one of them has issues, the whole thing fails. Makes sense really, so I try to isolate each archive I want in its own nzb file. That seems to work for me now, with no missed unraring of archives.

Happy Thanksgiving!

Hop

---

### Post by Mithrilhall on 2007-11-23
Did anyone get the "libNotify daemon" portion to work?

I had it working a while ago and had to rebuild and can't get it working again. I can't remember what I had to install to get it to work.

---

### Post by techno-wiz on 2007-12-06
The original post is quite old. Can this now be set up by installing from synaptic? I have installed it but not sure where to go to configure it.

---

### Post by kd7swh on 2007-12-06
Yes, its in Synaptic and now it supports SSL so you don't need stunnel anymore.
(If you need help you can message me)

---

### Post by sizzam on 2007-12-07
> **techno-wiz said:**
> The original post is quite old. Can this now be set up by installing from synaptic? I have installed it but not sure where to go to configure it.

The config file for the version from synaptic is at /etc/hellanzb.conf

---

### Post by kd7swh on 2007-12-07
[CENTER]**Update *****[/CENTER]

hellanzb is a great tool for downloading binaries from newsgroups. In the past, if you wanted to use hellanzb you had to compile it from source code. This is no longer necessary because a binary is available in the repository.

Method #1: The Easy Way

Step 1: Installing hellanzb

Type ```
sudo apt-get install hellanzb
``` in a terminal window.


Step 2: Configuring hellanzb

From the terminal, type: ```
gksudo gedit /etc/hellanzb.conf
```

This will open the configuration file.

You will need to edit it so your news server, username, password, and folders are correct. The provided file is well commented and should do a good job of explaining how to make these changes correctly.

I will provide a copy of the example hellanzb.conf in this post for reference.

Step 3: The download

After you have saved your hellanzb.conf file you'll be ready to go. Just run hellanzb from the terminal and place nzb files in the daemon.queue folder that you set in your hellanzb.conf file. 



Method #2: The Hard Way (Which really isn't that hard at all)

Setting up hellanzb from scratch isn't too hard.

Step 1: Dependencies

From the terminal, ```
sudo apt-get install python-dev python-twisted unrar par2
```

If you need SSL support it would look like this:

```
sudo apt-get install python-dev python-twisted unrar par2 openssl libssl-dev
```

Step 2: Downloading and Preparing hellanzb
 
Visit the hellanzb web page: [http://www.hellanzb.com/trac/](http://www.hellanzb.com/trac/)  and get the latest tarball.

When I wrote this hellanzb 0.13 was the latest version so these step apply to that version. If you are using a different version just change the version number, the steps are still the same.

Part 1: The download

From a terminal window: ```
wget http://www.hellanzb.com/distfiles/hellanzb-0.13.tar.gz
```

Part 2: Extract Tar File

In the same terminal window: ```
sudo tar -xzvf hellanzb-0.13.tar.gz
```

Part 3: Enter the newly created folder

In the same terminal window: ```
cd hellanzb-0.13
```

Step 3: Installing hellanzb

From the existing terminal window type: ```
python setup.py install
```

Step 4. Copy sample configuration file and configure hellanzb

Part 1: Copying

From the existing terminal window type: ```
sudo cp /usr/etc/hellanzb.conf.sample /usr/etc/hellanzb.conf
```

Part 2: Configuring

From the existing terminal window type: ```
gksudo gedit /usr/etc/hellanzb.conf
```

This will open the configuration file.

You will need to edit it so your news server, username, password, and folders are correct. The provided file is well commented and should do a good job of explaining how to make these changes correctly.

I will provide a copy of the example hellanzb.conf in this post for reference.

Step 5: The download

After you have saved your hellanzb.conf file you'll be ready to go. Just run hellanzb from the terminal by typing ```
sudo hellanzb.py
``` and place nzb files in the daemon.queue folder that you set in your hellanzb.conf file.



NOTES:

Alternatively you can install hellanzb through a subversion trunk. If you know what that is you most likely don't need directions on how to do it from me. 

hellanzb now supports ssl with the use of openssl so you no longer need to use stunnel to gain encryption.

You can use C-yenc to decode faster.

Many GUIs are available for hellanzb. Check [www.hellanzb.com/trac](www.hellanzb.com/trac) for the full list.

---

### Post by punking on 2007-12-23
When I run Hellanzb I get the following error. This is my first day using linux after years and years of XP. 

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

Does anybody know how I can solve this? Thanks.

---

### Post by TuxCrafter on 2007-12-23
> **punking said:**
> When I run Hellanzb I get the following error. This is my first day using linux after years and years of XP. 

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

Does anybody know how I can solve this? Thanks.

undo everything you have done to get hellanzb this way and try the script that its matching topic in my signature. Hope you get it working.

---

### Post by punking on 2007-12-23
Hi 

Thanks for the reply. I'll try the script. One quick question how do I make sure everything is removed as I installed it using the instructions on the first page.

I know, dumb, question but I'm ten years of windows, one day of linux, so it's not just a steep learning curve and more like being thrown off a cliff.

---

### Post by TuxCrafter on 2007-12-24
> **punking said:**
> Hi 

Thanks for the reply. I'll try the script. One quick question how do I make sure everything is removed as I installed it using the instructions on the first page.

I know, dumb, question but I'm ten years of windows, one day of linux, so it's not just a steep learning curve and more like being thrown off a cliff.

Try the remove option in the script I think they will be sufficient.

Also you can take a look at the script, so you can see what it actually does.

---

### Post by punking on 2007-12-24
> **TuxCrafter said:**
> Try the remove option in the script I think they will be sufficient.

Also you can take a look at the script, so you can see what it actually does.

Thanks. It's working. I had slight fumble when I forgot to change SSL to true and discovered that pyopenssl wasn't installed but now it's fine. Thanks again.

---

### Post by jumpslu7 on 2008-01-04
Great tutorial for installing from source!  You can also get hellanzb from apt now!  I've written [an init script]("http://belfastgeek.net/2008/01/03/hellanzb-init-script/") , so that hellanzb will survive a reboot.  There's also a tute on [how to get Hellaworld working with HellaNZB]("http://belfastgeek.net/2007/12/30/hellaworld/"), that'll enable you to drag and drop to rearrange nzb files in your queue!

Have fun!
j

---

### Post by Hopworks on 2008-01-06
> **benfindlay said:**
> To get rid of hellanzb just type ```
sudo apt-get remove hellanzb
``` into the terminal.

Hope this helps

OK, I did this, and some space was freed, but when I do a ```
find -name hella*
``` there are still a lot of things found.

I want to completely clean my Feisty of .12 so I can then install .13 (or latest version) from the repositories and move on. It's been awhile, but I'm fairly sure I tried this once already, then installed from the repositories, and was still at version .12 (sigh)

Do I have to manually delete everything I find doing a find -name hella*? or is there an easier and less dangerous way?

Hop

---

### Post by Hopworks on 2008-01-06
Well, I bashed the script, and it ran and gave me a set of options (in red) and one of the options was to remove hellanzb. I did that option, and then did a find -name hella* and these listed...
```
root@hopworks:/# find -name hella*
./ext2/nzb/hellanzbState.xml
./var/tmp/hellanzb.log
./var/lib/dpkg/info/hellanzb.list
./home/public/hella
./home/public/hella/hella_options.txt
./home/public/hli/hellanzb
./home/public/hli/hellanzb/hellanzb.sh
./usr/share/doc/hellanzb
./usr/lib/python2.5/site-packages/hellanzb-0.12.egg-info
./media/mythtv/backups/server/hellanzb-0.12
./media/mythtv/backups/server/hellanzb-0.12/build/scripts-2.5/hellanzb.py
./media/mythtv/backups/server/hellanzb-0.12/hellanzb.py
./media/mythtv/backups/server/hellanzb-0.12/etc/hellanzb.conf.sample
./media/mythtv/backups/hellanzb.sh
./etc/hellanzb.conf
```

So the remove doesn't work with manually installed legacy versions of hellanzb? That's cool, just want to know how to get rid of that older version so I can enjoy the newest version. :)

Hop

---

### Post by Hopworks on 2008-01-06
Just like magic, I post and then find my answer, I hope.

I was looking at that list of hits using FIND and everything looks like extra stuff I did, so I did an apt-get, and a lot more things happened than did before. I typed in hellanzb in the command line, and unlike before, it worked. I'll have to do a few things to see if the version changed, and see if it will work with my customized web interface, and look at the config and change the folder references, but I think I'm all good.

Hop

---

### Post by Thundercat on 2008-01-12
> **disturbedite said:**
> 
hellanzb v0.12 (config = /usr/etc/hellanzb.conf)
(news.qwest.net) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: 1171952904
Parsing: 1171952904.nzb...
Parsed: 1 files (18 posts), 6.8MB
Queued: 6.8MB
[1]
[2]
[3]
[4]
[Total] 0.0KB/s, 6 MB queued, ETA: 00:00:0


I was having the same problem until I found the other version of the conf file!
there is the one in /etc which I had configured correctly, but also one in ~/.hellanzb which overrides the /etc one.

Once I configured the second one the downloads began!

---

### Post by Thundercat on 2008-01-12
.

---

### Post by mpm on 2008-01-25
I think I have followed your instructions well but run into a problem. When I try to run the program hellanzb.py I get:
michael@michael:~/usr/hellanzb-0.9/etc$ hellanzb.py
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

Which means absolutely nothing to a novice like myself, any help would be appreciated.

---

### Post by mosegris on 2008-01-28
HellaNZB works beautifully for me, BUT only when my laptop is connected through cable. 
When I run in wireless mode I have the problem that the connection is lost to the news server and even though it still shows that I'm connected to the access point I cannot browse the web. It's like it freezes the connection. Then after 30 sec or so it re-connects and then again after 2 min. it freezes.
In the hellanzb log it says. "DNS lookup to news.mynewsserver.com failed".

Anybody have a clue whats going on. It's problably the configuration of the router which causes the problem? When I'm connected thorugh cable it is though plugged-in in the router.

Here is the log file

2008-01-24 17:51:42,751 [ThrottlingProtocol,client] <twisted.internet.tcp.Connector instance at 0x8912b2c> will retry in 11 seconds
2008-01-24 17:51:42,751 usenetserver[3] CONNECTION LOST
2008-01-24 17:51:42,752 usenetserver[3] requeueing segment: /home/tgl/nzb/daemon.working/megabuenos-byte4u.part022.rar.segment0090
2008-01-24 17:51:42,753 [ThrottlingProtocol,client] <twisted.internet.tcp.Connector instance at 0x89129ac> will retry in 19 seconds
2008-01-24 17:51:42,753 usenetserver[6] TIMING OUT connection
2008-01-24 17:51:42,754 usenetserver[6] CONNECTION LOST
2008-01-24 17:51:42,755 usenetserver[6] requeueing segment: /home/tgl/nzb/daemon.working/megabuenos-byte4u.part022.rar.segment0094
2008-01-24 17:51:42,755 [ThrottlingProtocol,client] <twisted.internet.tcp.Connector instance at 0x8912e2c> will retry in 32 seconds
2008-01-24 17:51:42,928 usenetserver[0] TIMING OUT connection
2008-01-24 17:51:42,929 usenetserver[0] CONNECTION LOST
2008-01-24 17:51:42,930 usenetserver[0] requeueing segment: /home/tgl/nzb/daemon.working/megabuenos-byte4u.part022.rar.segment0091
2008-01-24 17:51:42,931 [ThrottlingProtocol,client] <twisted.internet.tcp.Connector instance at 0x89125ac> will retry in 52 seconds
2008-01-24 17:51:42,932 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x891252c>
2008-01-24 17:51:42,932 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x891256c>
2008-01-24 17:51:44,288 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x891252c>
2008-01-24 17:51:44,289 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x891256c>
2008-01-24 17:52:14,296 [-] <twisted.internet.tcp.Connector instance at 0x8912fac> will retry in 70 seconds
2008-01-24 17:52:15,252 [-] <twisted.internet.tcp.Connector instance at 0x8912cac> will retry in 100 seconds
2008-01-24 17:52:15,470 usenetserver[0] CONNECTION MADE
2008-01-24 17:52:15,489 usenetserver[6] CONNECTION MADE
2008-01-24 17:52:15,509 usenetserver[3] CONNECTION MADE
2008-01-24 17:52:15,531 usenetserver[4] CONNECTION MADE
2008-01-24 17:52:15,539 usenetserver[2] CONNECTION MADE
2008-01-24 17:52:15,716 usenetserver[0] MODE READER successful

---

### Post by knowtheledge on 2008-02-03
Hi Guys

Heres hoping you can help. I have been using Hellanzb and Usenetserver and they were working fine. However, hellanzb now constantly sits as idle. 

I have tried re-installing Hellanzb, I have checked my news server address and account/password details and they are correct and with sufficient privileges 

I have no idea why it just sits as idle, does anyone know what could be wrong?

Cheers Guys

---

### Post by zamael on 2008-02-11
this is a complete newbie question... but how do I make it so Hellanzb will place processed files in a directory on a local disk and not someplace in my home directory?

I've tried all sort of changes to the conf file but can't get it to save to my secondary hard drive!  Thanks!

---

### Post by TuxCrafter on 2008-02-12
> **zamael said:**
> this is a complete newbie question... but how do I make it so Hellanzb will place processed files in a directory on a local disk and not someplace in my home directory?

I've tried all sort of changes to the conf file but can't get it to save to my secondary hard drive!  Thanks!

make sure you are configuring the correct config file, then change the following option to something like:
Hellanzb.PREFIX_DIR = '/media/sda3/downloads/'

---

### Post by zamael on 2008-02-12
> **TuxCrafter said:**
> make sure you are configuring the correct config file, then change the following option to something like:
Hellanzb.PREFIX_DIR = '/media/sda3/downloads/'

oh geez... I never thought of putting ALL the hellanzb files onto the local disk.  Thanks TuxCrafter!

---

### Post by romeyde on 2008-02-12
I've been using hellanzb (0.13) for a few months now and love it.  I have this issue though where it will just stop processing new files.  It just sits there twiddling it's thumbs.  I kill it and restart it (/etc/init.d/hellanzb start) and it will then process previously downloaded files.

---

### Post by Stefanic on 2008-02-13
> **romeyde said:**
> I've been using hellanzb (0.13) for a few months now and love it.  I have this issue though where it will just stop processing new files.  It just sits there twiddling it's thumbs.  I kill it and restart it (/etc/init.d/hellanzb start) and it will then process previously downloaded files.
I have the same problem.
Processing of new NZB's works fine, as well as downloading and par2 verifying. But when Hellanzb should unpack the rar files it just does nothing until you restart it.
Anyone got an idea why this is? Would be nice to have an unpacked file without having to restart.

---

### Post by romeyde on 2008-02-14
Perhaps as a stop gap fix, there is a way to force hellanzb to restart once a day?   I believe, based on my issues, that this would fix the problem.

---

### Post by Stefanic on 2008-02-15
I did some more testing.
Seems the not unrar-ing occurs only when hellanzb starts at boot.
When you restart it it works perfectly here.

---

### Post by NT4usB on 2008-02-15
When I first installed per this post, hellanzb started at boot and changed hellanzbState.xml to being owned by root then it wouldn't run at all.
Removed it from the startup, launch it manually and all is well.

---

### Post by troutbum13 on 2008-02-18
bump for the same problem with unrar not kicking in...the log shows
```

2008-02-18 12:46:37,641 INFO svd-tnmntb.par2: Verifying via par group: svd-tnmntb*.{par2,PAR2}..
2008-02-18 12:47:07,747 INFO svd-tnmntb.par2: Finished par verify (1 par group, took: 30s)
2008-02-18 12:47:07,930 INFO svd-tnmntb.par2: Unraring svd-tnmntb.rar..
2008-02-18 12:47:22,123 INFO svd-tnmntb.par2: Finished unraring (1 rar group, took: 14s)
2008-02-18 12:47:22,361 LOGFILE Deleting processed dir: svd-tnmntb.par2/processed, it contains: ['.par_done', '.rar_done', 'svd-tnmntb.par2', 'svd-tnmntb.par2.nzb', 'svd-tnmntb.r00', 'svd-tnmntb.r01', 'svd-tnmntb.r02', 'svd-tnmntb.r03', 'svd-tnmntb.r04', 'svd-tnmntb.r05', 'svd-tnmntb.r06', 'svd-tnmntb.r07', 'svd-tnmntb.r08', 'svd-tnmntb.r09', 'svd-tnmntb.r09.1', 'svd-tnmntb.r10', 'svd-tnmntb.r10.1', 'svd-tnmntb.r11', 'svd-tnmntb.r12', 'svd-tnmntb.r13', 'svd-tnmntb.r14', 'svd-tnmntb.r15', 'svd-tnmntb.r16', 'svd-tnmntb.r17', 'svd-tnmntb.r18', 'svd-tnmntb.r19', 'svd-tnmntb.r20', 'svd-tnmntb.r21', 'svd-tnmntb.r22', 'svd-tnmntb.r23', 'svd-tnmntb.r24', 'svd-tnmntb.r24.1', 'svd-tnmntb.r25', 'svd-tnmntb.r25.1', 'svd-tnmntb.r26', 'svd-tnmntb.r27', 'svd-tnmntb.r28', 'svd-tnmntb.r29', 'svd-tnmntb.r30', 'svd-tnmntb.r31', 'svd-tnmntb.r32', 'svd-tnmntb.r33', 'svd-tnmntb.r34', 'svd-tnmntb.r35', 'svd-tnmntb.r36', 'svd-tnmntb.r37', 'svd-tnmntb.r38', 'svd-tnmntb.r39', 'svd-tnmntb.r40', 'svd-tnmntb.r40.1', 'svd-tnmntb.r41', 'svd-tnmntb.r41.1', 'svd-tnmntb.r42', 'svd-tnmntb.r43', 'svd-tnmntb.r44', 'svd-tnmntb.r45', 'svd-tnmntb.r46', 'svd-tnmntb.rar', 'svd-tnmntb.sfv', 'svd-tnmntb.vol000+01.PAR2', 'svd-tnmntb.vol001+02.PAR2', 'svd-tnmntb.vol003+04.PAR2', 'svd-tnmntb.vol007+08.PAR2', 'svd-tnmntb.vol015+14.PAR2', 'svd-tnmntb.vol029+26.PAR2.segment0001', 'svd-tnmntb.vol055+51.PAR2.segment0001', 'svd-tnmntb.vol106+59.PAR2.segment0001', 'svd-tnmntb.vol165+59.PAR2.segment0001', 'svd-tnmntb.vol224+59.PAR2.segment0001']

``` 
And I get an empty directory in /home/user/.hellanzb/done

when I restart hellanzb

I get
```

2008-02-18 14:38:09,210 INFO 
2008-02-18 14:38:09,210 INFO hellanzb v0.13 (config = /etc/hellanzb.conf)
2008-02-18 14:38:09,268 LOGFILE (giganews1) Opening 8 connections...
2008-02-18 14:38:09,270 INFO hellanzb - Now monitoring queue...
2008-02-18 14:38:09,290 INFO Resuming post processor: svd-tnmntb.par2

```

Not sure what to make of it....

---

### Post by TuxCrafter on 2008-02-19
> **troutbum13 said:**
> bump for the same problem with unrar not kicking in...the log shows
```

2008-02-18 12:46:37,641 INFO svd-tnmntb.par2: Verifying via par group: svd-tnmntb*.{par2,PAR2}..
2008-02-18 12:47:07,747 INFO svd-tnmntb.par2: Finished par verify (1 par group, took: 30s)
2008-02-18 12:47:07,930 INFO svd-tnmntb.par2: Unraring svd-tnmntb.rar..
2008-02-18 12:47:22,123 INFO svd-tnmntb.par2: Finished unraring (1 rar group, took: 14s)
2008-02-18 12:47:22,361 LOGFILE Deleting processed dir: svd-tnmntb.par2/processed, it contains: ['.par_done', '.rar_done', 'svd-tnmntb.par2', 'svd-tnmntb.par2.nzb', 'svd-tnmntb.r00', 'svd-tnmntb.r01', 'svd-tnmntb.r02', 'svd-tnmntb.r03', 'svd-tnmntb.r04', 'svd-tnmntb.r05', 'svd-tnmntb.r06', 'svd-tnmntb.r07', 'svd-tnmntb.r08', 'svd-tnmntb.r09', 'svd-tnmntb.r09.1', 'svd-tnmntb.r10', 'svd-tnmntb.r10.1', 'svd-tnmntb.r11', 'svd-tnmntb.r12', 'svd-tnmntb.r13', 'svd-tnmntb.r14', 'svd-tnmntb.r15', 'svd-tnmntb.r16', 'svd-tnmntb.r17', 'svd-tnmntb.r18', 'svd-tnmntb.r19', 'svd-tnmntb.r20', 'svd-tnmntb.r21', 'svd-tnmntb.r22', 'svd-tnmntb.r23', 'svd-tnmntb.r24', 'svd-tnmntb.r24.1', 'svd-tnmntb.r25', 'svd-tnmntb.r25.1', 'svd-tnmntb.r26', 'svd-tnmntb.r27', 'svd-tnmntb.r28', 'svd-tnmntb.r29', 'svd-tnmntb.r30', 'svd-tnmntb.r31', 'svd-tnmntb.r32', 'svd-tnmntb.r33', 'svd-tnmntb.r34', 'svd-tnmntb.r35', 'svd-tnmntb.r36', 'svd-tnmntb.r37', 'svd-tnmntb.r38', 'svd-tnmntb.r39', 'svd-tnmntb.r40', 'svd-tnmntb.r40.1', 'svd-tnmntb.r41', 'svd-tnmntb.r41.1', 'svd-tnmntb.r42', 'svd-tnmntb.r43', 'svd-tnmntb.r44', 'svd-tnmntb.r45', 'svd-tnmntb.r46', 'svd-tnmntb.rar', 'svd-tnmntb.sfv', 'svd-tnmntb.vol000+01.PAR2', 'svd-tnmntb.vol001+02.PAR2', 'svd-tnmntb.vol003+04.PAR2', 'svd-tnmntb.vol007+08.PAR2', 'svd-tnmntb.vol015+14.PAR2', 'svd-tnmntb.vol029+26.PAR2.segment0001', 'svd-tnmntb.vol055+51.PAR2.segment0001', 'svd-tnmntb.vol106+59.PAR2.segment0001', 'svd-tnmntb.vol165+59.PAR2.segment0001', 'svd-tnmntb.vol224+59.PAR2.segment0001']

```And I get an empty directory in /home/user/.hellanzb/done

when I restart hellanzb

I get
```

2008-02-18 14:38:09,210 INFO 
2008-02-18 14:38:09,210 INFO hellanzb v0.13 (config = /etc/hellanzb.conf)
2008-02-18 14:38:09,268 LOGFILE (giganews1) Opening 8 connections...
2008-02-18 14:38:09,270 INFO hellanzb - Now monitoring queue...
2008-02-18 14:38:09,290 INFO Resuming post processor: svd-tnmntb.par2

```Not sure what to make of it....


you can make a bug ticked on the hellanzb website

---

### Post by Tobywaters on 2008-02-24
I am getting the following error when trying to get hellanzb to work, has anyone had any issues like this?

[PHP]hellanzb v0.13 (config = /etc/hellanzb.conf)
(changeme) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: test.nzb
[-] Unhandled Error
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/var/lib/python-support/python2.5/Hellanzb/Daemon.py", line 99, in recoverStateAndBegin
    scanQueueDir(True)
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 224, in scanQueueDir
    writeStateXML()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 408, in writeStateXML
    backupThenWrite()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 397, in backupThenWrite
    outFile = open(file, 'wb')
exceptions.IOError: [Errno 2] No such file or directory: '/media/sdc1/hellanzb//nzb/hellanzbState.xml'

[-] Unhandled Error
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 397, in backupThenWrite
    outFile = open(file, 'wb')
exceptions.IOError: [Errno 2] No such file or directory: '/media/sdc1/hellanzb//nzb/hellanzbState.xml'[/PHP]

---

### Post by mrbsee on 2008-02-26
I've got the latest Hellanzb installed using Synaptic.  It works great.  However, it does not extract the rar files.  How do I set up automatic extracting?  !  Also when I try to enable SSL I get an error about ssl not being installed how do I enable it?   Thanks in advance.

./EDIT
Figured out my SSL problem.. downloaded python open SSL and everything is great.  Auto extract was fixed by enabling it in the .conf problem solved.  I love this program!

---

### Post by rocketfu on 2008-02-27
I installed hellanzb from the stable repository with "apt-get" (version .13.2 

But when I add a *.nzb file to the queue folder hellanzb starts downloading it but the status is always idle. The download never actually starts. I checked the log file and there are no errors. 


Any ideas?

---

### Post by happydaddy on 2008-03-05
Hi guys

Thanks for the great how to, i am new to ubuntu and struggled to get hellanzb to work at first but with help from the how to's i managed to get it to work. Recently i purchased a new hard drive, installed it and set it up to carry all my media stuff. Problem however i don't know how to set the hellanzb to transfer the completed media  to my new drive media/sdb1 downloads folder. Please help.i tried opening the config folder and modifiying the script below  but all it does is create a folder in my home/happy directory  "sdb1/media/downloads". also is there a way i can delete these unnecessary folders created by my script below as it seemed to be locked.

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + '/sdb1/media/downloads/'

I also have a teamspeak server running and would like it to start up when the machine starts and not have to go to the terminal and type cd tss2_rc2 and then type  ./teamspeak2-server_startscript start

Thanks in advanced.

---

### Post by happydaddy on 2008-03-08
hi

after messing around with it i removed hellanzb and reinstalled it on my media/sdb1 drive. Problem was though that it was in root so i could not past nzb's into queue directory. I then used this command " gksudo nautilus " which allowed me to search for the hellanzb queue dir  and changed the properties and permissions from root to my user account.

Works like a bomb 

Thanks

---

### Post by kcobra on 2008-03-08
With hellanzb running in daemon mode is it possible to throttle the connection speed up and down on the fly? I know I can edit the "Hellanzb.MAX_RATE" entry in the counf file and then bounce the process but I was wanting something more slick.

Reason for wanting this is that when I am using my PC I don't want hellanzb sucking up all my bandwidth but when I am not on the computer I want hellanzb to download at full speed.

---

### Post by skap on 2008-03-10
Does anyone knows how to uninstall this?

---

### Post by Rizla on 2008-03-11
I got hellanzb working yesterday based on the initial setup in this post, come to find out after reading ALL 26 pages.  That its in the repo's now.  For the sake of easy managemnt, I want to remove all the files associated with hellanzb that I installed and configed yesterday.  Whats the best way to do this.

Ok, if you can bear with me I have to ask a stupid question.

HellaNZB is only the program used to download the NZB's correct?

In order to find the NZB's you want what site should you be searching?  I bought a giganews account yesterday and had config'd that with hellaNZB.

I guess I really want to know how to search for NZB's, do i need another program to do that?  I was using Pan and Klibido (sp?), but I dont think they're the right program to use in conjunction with hellaNZB.  Am I wrong.

Anyone have a basic overview to help me grasp the concept of newsgroups?  I'm coming for a bt world..:confused:


EDIT:

After doing some more reading around.  I think i get how it sort of works.  Ive been searching with newzleech.com and its been turning up some good results i see the option to save nzb.  I take it I just drop that file into the daemon.queue folder of hellanzb?  Also, are there any other sites similar to newzleech.com that have good results?  Is this one of those hush hush topics that no one likes to share?

---

### Post by Mithrilhall on 2008-03-12
The best sites that I've seen for NZB's are paid sites.

I believe these are free (just a few to get you started):

[http://nzbmatrix.com/index.php](http://nzbmatrix.com/index.php)
[http://alt.binaries.nl/](http://alt.binaries.nl/)
[http://www.binarynewz.com/](http://www.binarynewz.com/)

---

### Post by BassKozz on 2008-03-12
> **kd7swh said:**
> 
hellanzb now supports ssl with the use of openssl so you no longer need to use stunnel to gain encryption.
I just switched my Usenet provider plan to support SSL so I want to take advantage of it, but I can't get SSL to work, I did install ***python-pyopenssl*** but I am still having trouble getting it to work...
here is what my debug log looks like:
```

2008-03-12 22:45:57,005 [-] Log opened.
2008-03-12 22:45:57,008 hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
2008-03-12 22:45:57,011 [-] twisted.web.server.Site starting on 8760
2008-03-12 22:45:57,012 [-] Starting factory <twisted.web.server.Site instance at 0x881a7ec>
2008-03-12 22:45:57,119 Using: Twisted-2.5.0, TwistedWeb-0.7.0
2008-03-12 22:45:57,120 python: 2.5.1 (r251:54863, Mar  7 2008, 04:10:12) 
2008-03-12 22:45:57,121 [GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]
2008-03-12 22:45:57,121 os: Linux-2.6.22-14-generic (i686)
2008-03-12 22:45:57,124 initFillServers: fillserver support disabled
2008-03-12 22:45:57,126 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:57,127 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:57,230 recoverStateFromDisk recovered: RecoveredState: version: 0.13 newzbinCookie keys: []
downloading: {u'Beginning Ubuntu Linux From Novice To Professional': {u'category': u'Books', u'totalBytes': u'24053253', u'id': 0, u'name': u'Beginning Ubuntu Linux From Novice To Professional'}}
processing: {}
queued: {u'Ubuntu Linux Toolbox: 1000+ Commands For Ubuntu and Debian Power Users': {u'category': u'Books', u'totalBytes': u'2340719', 'order': 0, u'id': 1, u'name': u'Ubuntu Linux Toolbox: 1000+ Commands For Ubuntu and Debian Power Users '}}
2008-03-12 22:45:57,656 stdinEchoOff - OFF
2008-03-12 22:45:57,717 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:57,720 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:57,723 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:57,816 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,819 NewsHostin[4] CONNECTION MADE
2008-03-12 22:45:57,823 NewsHostin[5] CONNECTION MADE
2008-03-12 22:45:57,827 NewsHostin[6] CONNECTION MADE
2008-03-12 22:45:57,831 NewsHostin[4] CONNECTION LOST
2008-03-12 22:45:57,832 NewsHostin[4] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,834 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bdec> will retry in 1 seconds
2008-03-12 22:45:57,836 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:57,837 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,838 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bb0c> will retry in 3 seconds
2008-03-12 22:45:57,840 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,841 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,842 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b84c> will retry in 4 seconds
2008-03-12 22:45:57,846 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,848 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:57,849 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,850 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b9ac> will retry in 10 seconds
2008-03-12 22:45:57,852 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:57,853 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,866 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bc6c> will retry in 16 seconds
2008-03-12 22:45:57,869 NewsHostin[6] CONNECTION LOST
2008-03-12 22:45:57,870 NewsHostin[6] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,871 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896328c> will retry in 18 seconds
2008-03-12 22:45:57,873 NewsHostin[5] CONNECTION LOST
2008-03-12 22:45:57,875 NewsHostin[5] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,876 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bf6c> will retry in 22 seconds
2008-03-12 22:45:57,878 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,879 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,880 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896310c> will retry in 41 seconds
2008-03-12 22:45:57,890 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,893 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,894 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,895 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896344c> will retry in 76 seconds
2008-03-12 22:45:57,915 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,952 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,953 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,954 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896360c> will retry in 135 seconds
2008-03-12 22:45:57,959 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,963 NewsHostin[5] CONNECTION MADE
2008-03-12 22:45:57,966 NewsHostin[6] CONNECTION MADE
2008-03-12 22:45:57,969 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:57,973 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:57,976 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,977 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,978 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89637cc> will retry in 112 seconds
2008-03-12 22:45:57,980 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,983 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:58,018 NewsHostin[5] CONNECTION LOST
2008-03-12 22:45:58,019 NewsHostin[5] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,020 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963d0c> will retry in 117 seconds
2008-03-12 22:45:58,022 NewsHostin[6] CONNECTION LOST
2008-03-12 22:45:58,023 NewsHostin[6] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,024 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896398c> will retry in 146 seconds
2008-03-12 22:45:58,028 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:58,028 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,029 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963b4c> will retry in 122 seconds
2008-03-12 22:45:58,031 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:58,032 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,033 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896726c> will retry in 103 seconds
2008-03-12 22:45:58,035 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:58,036 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,038 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963ecc> will retry in 71 seconds
2008-03-12 22:45:58,040 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:58,041 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,042 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89670ac> will retry in 133 seconds
2008-03-12 22:45:58,053 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:58,059 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:58,064 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:58,076 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:58,077 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,116 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89675ec> will retry in 104 seconds
2008-03-12 22:45:58,118 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:58,119 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,120 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89677ac> will retry in 117 seconds
2008-03-12 22:45:58,122 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:58,123 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,124 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896742c> will retry in 125 seconds
2008-03-12 22:45:58,124 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:58,125 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:59,514 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:59,515 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:59,552 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:59,573 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:59,574 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:59,575 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bdec> will retry in 116 seconds
2008-03-12 22:45:59,576 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:59,577 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:00,950 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:00,951 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:00,992 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:01,015 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:01,016 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:01,017 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bb0c> will retry in 108 seconds
2008-03-12 22:46:01,018 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:01,019 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:02,790 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:02,791 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:02,823 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:02,849 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:02,850 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:02,851 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b84c> will retry in 116 seconds
2008-03-12 22:46:02,852 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:02,853 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:08,258 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:08,259 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:08,292 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:08,314 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:08,314 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:08,315 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b9ac> will retry in 147 seconds
2008-03-12 22:46:08,316 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:08,317 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:13,350 [twisted.web.server.Site] (Port 8760 Closed)
2008-03-12 22:46:13,351 [twisted.web.server.Site] Stopping factory <twisted.web.server.Site instance at 0x881a7ec>

```
I Assume the: 
**lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]]** 
lines have something to do with it... but what does this mean and how can I fix?

---

### Post by romeyde on 2008-03-13
Still having the stupido refusing to unpack downloads issue.   On a clean boot, hellanzb starts up automatically and all looks good.

root      5183     1  0 16:04 ?        00:00:00 /usr/bin/SCREEN -S hellanzb -d -m /usr/bin/hellanzb
root      5212  5183  0 16:04 pts/0    00:00:32 /usr/bin/python /usr/bin/hellanzb


I download something and that goes fine but hellanzb just refuses to unpack it.

One thing I did just now notice though is that when it starts up on boot, it is writing to the /root/.hellanzb/log file.   When I kill it then restart it with sudo it then writes to my home directories log file.  It downloads fine when writing to roots log but won't unpack.

Something I can change so it starts up correctly?  Should it even be running as root?   Wouldn't mind having it start up under my account instead.

---

### Post by BassKozz on 2008-03-16
> **B/-\ssKozz said:**
> I just switched my Usenet provider plan to support SSL so I want to take advantage of it, but I can't get SSL to work, I did install ***python-pyopenssl*** but I am still having trouble getting it to work...
here is what my debug log looks like:
```

2008-03-12 22:45:57,005 [-] Log opened.
2008-03-12 22:45:57,008 hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
2008-03-12 22:45:57,011 [-] twisted.web.server.Site starting on 8760
2008-03-12 22:45:57,012 [-] Starting factory <twisted.web.server.Site instance at 0x881a7ec>
2008-03-12 22:45:57,119 Using: Twisted-2.5.0, TwistedWeb-0.7.0
2008-03-12 22:45:57,120 python: 2.5.1 (r251:54863, Mar  7 2008, 04:10:12) 
2008-03-12 22:45:57,121 [GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]
2008-03-12 22:45:57,121 os: Linux-2.6.22-14-generic (i686)
2008-03-12 22:45:57,124 initFillServers: fillserver support disabled
2008-03-12 22:45:57,126 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:57,127 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:57,230 recoverStateFromDisk recovered: RecoveredState: version: 0.13 newzbinCookie keys: []
downloading: {u'Beginning Ubuntu Linux From Novice To Professional': {u'category': u'Books', u'totalBytes': u'24053253', u'id': 0, u'name': u'Beginning Ubuntu Linux From Novice To Professional'}}
processing: {}
queued: {u'Ubuntu Linux Toolbox: 1000+ Commands For Ubuntu and Debian Power Users': {u'category': u'Books', u'totalBytes': u'2340719', 'order': 0, u'id': 1, u'name': u'Ubuntu Linux Toolbox: 1000+ Commands For Ubuntu and Debian Power Users '}}
2008-03-12 22:45:57,656 stdinEchoOff - OFF
2008-03-12 22:45:57,717 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:57,720 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:57,723 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:57,816 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,819 NewsHostin[4] CONNECTION MADE
2008-03-12 22:45:57,823 NewsHostin[5] CONNECTION MADE
2008-03-12 22:45:57,827 NewsHostin[6] CONNECTION MADE
2008-03-12 22:45:57,831 NewsHostin[4] CONNECTION LOST
2008-03-12 22:45:57,832 NewsHostin[4] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,834 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bdec> will retry in 1 seconds
2008-03-12 22:45:57,836 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:57,837 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,838 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bb0c> will retry in 3 seconds
2008-03-12 22:45:57,840 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,841 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,842 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b84c> will retry in 4 seconds
2008-03-12 22:45:57,846 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,848 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:57,849 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,850 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b9ac> will retry in 10 seconds
2008-03-12 22:45:57,852 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:57,853 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,866 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bc6c> will retry in 16 seconds
2008-03-12 22:45:57,869 NewsHostin[6] CONNECTION LOST
2008-03-12 22:45:57,870 NewsHostin[6] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,871 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896328c> will retry in 18 seconds
2008-03-12 22:45:57,873 NewsHostin[5] CONNECTION LOST
2008-03-12 22:45:57,875 NewsHostin[5] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,876 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bf6c> will retry in 22 seconds
2008-03-12 22:45:57,878 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,879 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,880 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896310c> will retry in 41 seconds
2008-03-12 22:45:57,890 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,893 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,894 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,895 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896344c> will retry in 76 seconds
2008-03-12 22:45:57,915 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,952 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,953 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,954 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896360c> will retry in 135 seconds
2008-03-12 22:45:57,959 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,963 NewsHostin[5] CONNECTION MADE
2008-03-12 22:45:57,966 NewsHostin[6] CONNECTION MADE
2008-03-12 22:45:57,969 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:57,973 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:57,976 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:57,977 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:57,978 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89637cc> will retry in 112 seconds
2008-03-12 22:45:57,980 NewsHostin[3] CONNECTION MADE
2008-03-12 22:45:57,983 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:58,018 NewsHostin[5] CONNECTION LOST
2008-03-12 22:45:58,019 NewsHostin[5] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,020 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963d0c> will retry in 117 seconds
2008-03-12 22:45:58,022 NewsHostin[6] CONNECTION LOST
2008-03-12 22:45:58,023 NewsHostin[6] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,024 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896398c> will retry in 146 seconds
2008-03-12 22:45:58,028 NewsHostin[3] CONNECTION LOST
2008-03-12 22:45:58,028 NewsHostin[3] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,029 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963b4c> will retry in 122 seconds
2008-03-12 22:45:58,031 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:58,032 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,033 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896726c> will retry in 103 seconds
2008-03-12 22:45:58,035 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:58,036 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,038 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x8963ecc> will retry in 71 seconds
2008-03-12 22:45:58,040 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:58,041 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,042 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89670ac> will retry in 133 seconds
2008-03-12 22:45:58,053 NewsHostin[0] CONNECTION MADE
2008-03-12 22:45:58,059 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:58,064 NewsHostin[2] CONNECTION MADE
2008-03-12 22:45:58,076 NewsHostin[0] CONNECTION LOST
2008-03-12 22:45:58,077 NewsHostin[0] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,116 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89675ec> will retry in 104 seconds
2008-03-12 22:45:58,118 NewsHostin[2] CONNECTION LOST
2008-03-12 22:45:58,119 NewsHostin[2] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,120 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x89677ac> will retry in 117 seconds
2008-03-12 22:45:58,122 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:58,123 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:58,124 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x896742c> will retry in 125 seconds
2008-03-12 22:45:58,124 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:58,125 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:59,514 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:59,515 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:45:59,552 NewsHostin[1] CONNECTION MADE
2008-03-12 22:45:59,573 NewsHostin[1] CONNECTION LOST
2008-03-12 22:45:59,574 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:45:59,575 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bdec> will retry in 116 seconds
2008-03-12 22:45:59,576 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:45:59,577 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:00,950 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:00,951 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:00,992 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:01,015 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:01,016 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:01,017 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895bb0c> will retry in 108 seconds
2008-03-12 22:46:01,018 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:01,019 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:02,790 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:02,791 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:02,823 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:02,849 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:02,850 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:02,851 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b84c> will retry in 116 seconds
2008-03-12 22:46:02,852 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:02,853 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:08,258 [-] Starting factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:08,259 [-] Starting factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:08,292 NewsHostin[1] CONNECTION MADE
2008-03-12 22:46:08,314 NewsHostin[1] CONNECTION LOST
2008-03-12 22:46:08,314 NewsHostin[1] lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]
]
2008-03-12 22:46:08,315 [ThrottlingProtocol,client] <twisted.internet.ssl.Connector instance at 0x895b9ac> will retry in 147 seconds
2008-03-12 22:46:08,316 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.Protocol.NZBLeecherFactory instance at 0x895b70c>
2008-03-12 22:46:08,317 [ThrottlingProtocol,client] Stopping factory <Hellanzb.NZBLeecher.NZBLeecherUtil.HellaThrottlingFactory instance at 0x895b7cc>
2008-03-12 22:46:13,350 [twisted.web.server.Site] (Port 8760 Closed)
2008-03-12 22:46:13,351 [twisted.web.server.Site] Stopping factory <twisted.web.server.Site instance at 0x881a7ec>

```
I Assume the: 
**lost connection: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_GET_RECORD', 'wrong version number')]]** 
lines have something to do with it... but what does this mean and how can I fix?

**_EDIT:**_ Figured it out, I had to set the host to port 563](*,)

---

### Post by iGeorgie on 2008-03-19
I've got the thing working and I'm very impressed.

I use it with HellaPHP. Also a very small/tiny/little program to use it through the webbrowser.

I've just a small problem. Since I'm a rookie on linux, I don't understand anything about ownerships/chmod or whatever...
What persmissions do I need on the queue-folder to upload .NZB's  through the webinterface? I got it working to upload, but then the ownership or permissions on the file isn't correct and HellaNZB can't handle it. When I put it there by hand, it works great.

EDIT:
I got it to work.
I ran the command: sudo chmod -R 777 'daemon.queue'
I also followed the instructions for automatic startup script. And it worked.
So now I published my internal website via SSLExplorer on the outside. It is now authenticated and secure.

---

### Post by honeydew on 2008-03-19
> **Rizla said:**
> 
After doing some more reading around.  I think i get how it sort of works.  Ive been searching with newzleech.com and its been turning up some good results i see the option to save nzb.  I take it I just drop that file into the daemon.queue folder of hellanzb?  Also, are there any other sites similar to newzleech.com that have good results?  Is this one of those hush hush topics that no one likes to share?

[http://newzbin.com](http://newzbin.com) I think is the best tons of retention and finds almost everything I am looking for.  Also it costs like $2 for 2 months.. or something rediculous.

also, hellafox works great with newzbin.. which enables right click queing for nzb's at newzbin =]

---

### Post by deadjones on 2008-04-02
hellanzb is the shiznit!  i've been using it for close to a year now.   recently i started playing with the tv downloaders. after some trial and erorr, i focused on prenominalNZB which i find to work so much better than the others listed on hella's site.  i have about 23 tv shows that i watch somewhat regularly and this script grabs a new episode everytime it's posted on newzbin.

well, it grabs the nzb and puts it in the hellanzb watched dir, which since having hellanzb running as daemon, is always watched. 

im now playing with rss news scrollers for both seamonkey and firefox to feed whats new in my fav movies newsgroups. so far, inforss is the best firefox addon (and seamonkey too) for this purpose. the others have to load a separate window. now if i see a movie i want, i just click on it (on the scroll) and it'll open a 'save as' dialog window for the nzb file. 

here's a tip:
if you want to put your 'watched' dir on your desktop, edit this line accordingly in the hellanzb.conf file:
(it's also nice to have your nzb-drop-dir and output-dir in your /home area, to get around those pesky 'ownership' issues. but if you install with apt or other package manager, it'll generally put it all in your /home/<user>/.hellanzb)

# Where to put queued .nzb filessh
Hellanzb.QUEUE_DIR = '/home/<user>/Desktop/NZB/'

if you'd like a custom output dir, such as /home/<user>/usenet (or whatever path you prefer) then find and edit this line in the conf:

# Where the fully processed archives go
Hellanzb.DEST_DIR = '/home/<user>/usenet/'

since the hellanzb.conf is in /etc/hellanzb.conf you'll have to open a console and type: sudo gedit /etc/hellanzb.conf 
if you're prompted to install gedit then install gedit and then try again. 


if you're looking for NZB's .. 

newzbin is good for recently posted stuff.  although they say they have a 200 day retention, try searching for something that you 'know' was posted just 90 days ago.  or even 20 days ago in many cases. can't find it. 
it's great for newly posted stuff to vcdquality.com usually but often still i'm charged with having to resort to an alternate for the 'newest' stuff.  
now, binsearch.info is a truly magnificent site. 199 days retention and it's really 199 days. oh yeah, and its free.  but as things stand now, if you want an auto tv downloader that works with hellanzb (so far as i can find, and i've searched around) the only site that'll work with them is newzbin.  nb is something like .50 cents a week for 8 weeks until renew. 

if newzbin and binsearch.info cant find it, try newzleech.com as an alternate. i've found that newzleech lists stuff that i couldnt find anywhere else. you can even choose the first and last file in a series and then click the 'range' option to auto select all the ones in between (much like the news site easynews).  but nl's interface has some to be desired for.

hope some of this helps



Party on Bill & Ted

---

### Post by nchase on 2008-04-04
Hey, last night I wrote a guide to using the LottaNZB GTK frontend with HellaNZB -- you can read it [here]("http://blog.ahfr.org/2008/04/newsgroup-binaries-with-hellanzb-and.html"). Hope it helps someone!

---

### Post by romeyde on 2008-04-04
> **nchase said:**
> Hey, last night I wrote a guide to using the LottaNZB GTK frontend with HellaNZB -- you can read it [here]("http://blog.ahfr.org/2008/04/newsgroup-binaries-with-hellanzb-and.html"). Hope it helps someone!

I don't get this part of your guide:


*If you want this setup to automagically extract your rar files for you, go to the hellanzb.conf file (open terminal, run command: "gedit .lottanzb/hellanzb.conf") and change "Hellanzb.SKIP_UNRAR = False" to "Hellanzb.SKIP_UNRAR = True". change "Hellanzb.UNRAR_CMD = False" to "Hellanzb.UNRAR_CMD = "/usr/bin/unrar""

Don't you want Hellanzb.SKIP_UNRAR to equal False?

---

### Post by nchase on 2008-04-05
> **romeyde said:**
> I don't get this part of your guide:


*If you want this setup to automagically extract your rar files for you, go to the hellanzb.conf file (open terminal, run command: "gedit .lottanzb/hellanzb.conf") and change "Hellanzb.SKIP_UNRAR = False" to "Hellanzb.SKIP_UNRAR = True". change "Hellanzb.UNRAR_CMD = False" to "Hellanzb.UNRAR_CMD = "/usr/bin/unrar""

Don't you want Hellanzb.SKIP_UNRAR to equal False?

Thanks for catching that -- it should be the other way around

---

### Post by cchester on 2008-04-06
Thanks for your guide. With hellanzb in the repos and lottanzb having a ubuntu package to make installing easier it is now becoming easier to get a nzb client install and up and running that does everything seemlessly.

---

### Post by romeyde on 2008-04-09
Still have this annoying issue with hellanzb when I first boot.   hellanzb starts fine and will download anything in the queue just fine, but, it refuses to actually unrar when done.   The only way to fix this is to kill it and then restart it "sudo /etc/init.d/hellanzb start".  

On boot, when it starts up, it writes to /root/.hellanzb/log.   After killing and restarting it using sudo, it writes to the .hellanzb log in my home directory.  Today, after booting, this is what was written to roots log.  Perhaps those DNS errors have something to do with it?   I never see those in my own log after restarting it. 

2008-04-09 15:12:32,575 INFO 
2008-04-09 15:12:32,575 INFO hellanzb v0.13 (config = /etc/hellanzb.conf)
2008-04-09 15:12:32,712 LOGFILE (giganews) Opening 4 connections...
2008-04-09 15:12:32,739 INFO hellanzb - Now monitoring queue...
2008-04-09 15:12:32,897 INFO Resuming post processor: The Job
2008-04-09 15:12:33,075 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:33,077 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:33,082 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:33,084 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:34,424 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:35,195 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:36,606 ERROR DNS lookup failed for hostname: news.giganews.com
2008-04-09 15:12:37,442 ERROR DNS lookup failed for hostname: news.giganews.com

---

### Post by romeyde on 2008-04-12
grumble grumble grumble...

Something is broke with hellanzb.   Now, when I add something to the queue, it see's it, logs it but then just sits there.   Can't figure out why it won't actually start downloading it.   Last time it did something like this, it ended up being because I was over my giganews limit but that isn't the issue this time.

Tried killing and restarting multiple times, tried clearing the queue, even tried just removing the giganewsnzb directory and restarting it so it recreated all it's work directories.   Still no go.  When I add to the queue, this is all that gets entered into the log and then it just sits...   Ideas?  Is there another log file available that may have more info?

2008-04-12 20:35:27,151 INFO hellanzb v0.13 (config = /etc/hellanzb.conf)
2008-04-12 20:35:27,171 LOGFILE (giganews) Opening 4 connections...
2008-04-12 20:35:27,173 INFO hellanzb - Now monitoring queue...
2008-04-12 20:35:59,494 INFO Downloading newzbin NZB: 2991337 
2008-04-12 20:36:00,712 INFO Found new nzb (msgid: 2991337, category: Movies): TheSig
2008-04-12 20:36:02,197 INFO Downloading: TheSig
2008-04-12 20:36:02,239 INFO Parsing: 2991337_TheSig.nzb...
2008-04-12 20:36:02,514 INFO Parsed: 96 files (2133 posts), 1310.6MB
2008-04-12 20:36:02,585 INFO Queued: 1310.6MB

-----

Nevermind...  turned on debugging and it ended up that I was having giganews issue, CC on file expired...

---

### Post by revelation_21 on 2008-04-26
> **romeyde said:**
> grumble grumble grumble...

Something is broke with hellanzb.   Now, when I add something to the queue, it see's it, logs it but then just sits there.   Can't figure out why it won't actually start downloading it.   Last time it did something like this, it ended up being because I was over my giganews limit but that isn't the issue this time.

Tried killing and restarting multiple times, tried clearing the queue, even tried just removing the giganewsnzb directory and restarting it so it recreated all it's work directories.   Still no go.  When I add to the queue, this is all that gets entered into the log and then it just sits...   Ideas?  Is there another log file available that may have more info?


I am having this same issue. This started before I upgraded to 8.04. I have tried restarting the daemon and reinstalling hellanzb. It just sits there doing nothing or downloads at 5KB/s. Klibido will max out my link speed. Any ideas would be great.

---

### Post by Jaap28 on 2008-04-28
I have the following problem with Hellanzb. When i try to start the program in console i get the following error:

hellanzb v0.13 (config = /usr/etc/hellanzb.conf, C yenc module)
Exiting: FatalError'>: Unable to create directory for option: Hellanzb.POSTPONED _DIR dirName: /ext2/nzb/daemon.postponed/ error: [Errno 13] Permission denied: ' /ext2'

I use ubuntu through wubi.

Hope can anybody help me with this problem.

---

### Post by bvanaerde on 2008-04-29
> **Jaap28 said:**
> I have the following problem with Hellanzb. When i try to start the program in console i get the following error:

hellanzb v0.13 (config = /usr/etc/hellanzb.conf, C yenc module)
Exiting: FatalError'>: Unable to create directory for option: Hellanzb.POSTPONED _DIR dirName: /ext2/nzb/daemon.postponed/ error: [Errno 13] Permission denied: ' /ext2'

I use ubuntu through wubi.

Hope can anybody help me with this problem.

This is probably because there's an error in the HOWTO, at step 8:
You need to edit

> /usr/etc/hellanzb.conf
and not
> /usr/etc/hellanzb.conf.sample

---

### Post by Luke1972 on 2008-05-01
> **Tobywaters said:**
> I am getting the following error when trying to get hellanzb to work, has anyone had any issues like this?

[PHP]hellanzb v0.13 (config = /etc/hellanzb.conf)
(changeme) Opening 4 connections...
hellanzb - Now monitoring queue...
Found new nzb: test.nzb
[-] Unhandled Error
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 561, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/var/lib/python-support/python2.5/Hellanzb/Daemon.py", line 99, in recoverStateAndBegin
    scanQueueDir(True)
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 224, in scanQueueDir
    writeStateXML()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 408, in writeStateXML
    backupThenWrite()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 397, in backupThenWrite
    outFile = open(file, 'wb')
exceptions.IOError: [Errno 2] No such file or directory: '/media/sdc1/hellanzb//nzb/hellanzbState.xml'

[-] Unhandled Error
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/Hellanzb/Daemon.py", line 114, in initDaemon
    startNZBLeecher()
  File "/var/lib/python-support/python2.5/Hellanzb/NZBLeecher/__init__.py", line 262, in startNZBLeecher
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 220, in run
    self.mainLoop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 228, in mainLoop
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/var/lib/python-support/python2.5/Hellanzb/NZBQueue.py", line 397, in backupThenWrite
    outFile = open(file, 'wb')
exceptions.IOError: [Errno 2] No such file or directory: '/media/sdc1/hellanzb//nzb/hellanzbState.xml'[/PHP]





Yes I've had a similar problem.  Whilst I'm not a power user it seems that Hellanzb is starting up and wanted to carry on a download/unrar but the state of the files it was expecting doesn't match up to how the files actually are.  This confuses Hellanzb and it "freezes".  The log file shows just the same info so isn't very useful in this case.

To resolve this I deleted the NZB from the daemon.current directory and all the files associated with that NZB from the daemon.working directory too and restarted Hellanzb.  It happily carried on processing the daemon.queue directory with no troubles at all after that but I didn't try to process the same nzb again  (more as I'd changed my mind by then than fear of it happening again).

Good luck.

---

### Post by gedekran on 2008-05-03
How does one get hellanzb to process zipped nzb files?

I tried searching, played around with the conf file, read every page of this thread and still haven't figured it out.

Found this section in the conf file, but not sure how to configure it to process zipped nzb files.


```
# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
Hellanzb.NZB_ZIPS = '.nzb.zip'
```

Thanks.

---

### Post by pabloikba on 2008-05-03
I am new to this and am trying to get hellanzb to work...it seems to start because when I run it I see this:

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...

but when I drop an NZB file into the daemon.que directory...nothing ever happens....I'm sure I am doing something wrong but I have no idea what.

Attached is my hellanzb.conf file...

If anyone can lend me assistance I would be appreciative.

Thanks,
Pablo

---

### Post by Fuzzy_Logic on 2008-05-03
I followed the guide, but when I try to run the application I get the following output:

> Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_hellanzb.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

It might have been resolved earlier in this thread, and if so, I apologize, but I was to lazy to read through more than 30 pages of replies, I only skimmed through about ten pages...
Anyway, has anyone else encountered this problem, or maybe someone is skilled enough to be able to see a solution from seeing the output?
Thanks in advance! :)

---

### Post by bsg007 on 2008-05-03
> **pabloikba said:**
> I am new to this and am trying to get hellanzb to work...it seems to start because when I run it I see this:

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...

but when I drop an NZB file into the daemon.que directory...nothing ever happens....I'm sure I am doing something wrong but I have no idea what.

Attached is my hellanzb.conf file...

If anyone can lend me assistance I would be appreciative.

Thanks,
Pablo

```
# Hellanzb.PREFIX_DIR = 'home/zack/Desktop/NZB/'
```


Remove that comment.

---

### Post by bsg007 on 2008-05-03
> **Fuzzy_Logic said:**
> I followed the guide, but when I try to run the application I get the following output:



It might have been resolved earlier in this thread, and if so, I apologize, but I was to lazy to read through more than 30 pages of replies, I only skimmed through about ten pages...
Anyway, has anyone else encountered this problem, or maybe someone is skilled enough to be able to see a solution from seeing the output?
Thanks in advance! :)


Just install hellanzb from the repos. Make sure universe is enabled in System>Administration>Software Sources.

```
sudo apt-get install hellanzb
```

Edit /etc/hellanzb.conf with your settings. Run in terminal simply by typing hellanzb.

---

### Post by pabloikba on 2008-05-03
> **bsg007 said:**
> ```
# Hellanzb.PREFIX_DIR = 'home/zack/Desktop/NZB/'
```


Remove that comment.

Thanks for your reply. Here is what I am getting now (it seems to be stalled at this point):

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...
Found new nzb (msgid: 3037325): McHale's Navy - 3x03 - It's a Mad, Mad, Mad War
Resuming: McHale's Navy - 3x02 - Lester, the Skipper
Parsing: 3037326_McHale's Navy - 3x02 - Lester, the Skipper.nzb...
Parsed: 16 files (511 posts), 188.5MB
Queued: 188.5MB
[01]
[02]
[03]
[04]
[05]
[06]
[07]
[08]
[09]
[10]
[Total] 0.0KB/s, 188 MB queued, ETA: 00:00:00

And here is the logfile for this:

2008-05-04 00:36:34,779 INFO 
2008-05-04 00:36:34,781 INFO hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
2008-05-04 00:36:34,890 LOGFILE (giganews) Opening 10 connections...
2008-05-04 00:36:34,943 INFO hellanzb - Now monitoring queue...
2008-05-04 00:36:35,047 INFO Found new nzb (msgid: 3037325): McHale's Navy - 3x03 - It's a Mad, Mad, Mad War
2008-05-04 00:36:35,049 INFO Resuming: McHale's Navy - 3x02 - Lester, the Skipper
2008-05-04 00:36:35,109 INFO Parsing: 3037326_McHale's Navy - 3x02 - Lester, the Skipper.nzb...
2008-05-04 00:36:35,292 INFO Parsed: 16 files (511 posts), 188.5MB
2008-05-04 00:36:35,343 INFO Queued: 188.5MB

Any suggestions?

Pablo

---

### Post by nomad980 on 2008-05-04
I been using hellanzb for a while now, and decided it was time for me to run it as a daemon. I tried using the latest init script Dedors posted. I have yet to get it to work, it just starts and dies right there and then.

---

### Post by pabloikba on 2008-05-05
> **nomad980 said:**
> I been using hellanzb for a while now, and decided it was time for me to run it as a daemon. I tried using the latest init script Dedors posted. I have yet to get it to work, it just starts and dies right there and then.

See my post directly above yours....I got that far and it just sits there...hoping someone will help me...but, part of the problem I had was dropping the nzb into the wrong directory...I wound up with two sets of identical directories in two different places....the correct location is /home/xxxxx/.hellanzb/ for the directories and the conf file is in /etc/ ... hope that helps you...

Pablo

---

### Post by Fuzzy_Logic on 2008-05-05
> **bsg007 said:**
> Just install hellanzb from the repos. Make sure universe is enabled in System>Administration>Software Sources.

```
sudo apt-get install hellanzb
```

Edit /etc/hellanzb.conf with your settings. Run in terminal simply by typing hellanzb.

no luck... :-( I get the same output as before

---

### Post by pabloikba on 2008-05-05
> **Fuzzy_Logic said:**
> no luck... :-( I get the same output as before

It would seem like there has to be someone out there that can help Fuzzy and me.....

---

### Post by Luke1972 on 2008-05-13
> **pabloikba said:**
> Thanks for your reply. Here is what I am getting now (it seems to be stalled at this point):

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...
Found new nzb (msgid: 3037325): McHale's Navy - 3x03 - It's a Mad, Mad, Mad War
Resuming: McHale's Navy - 3x02 - Lester, the Skipper
Parsing: 3037326_McHale's Navy - 3x02 - Lester, the Skipper.nzb...
Parsed: 16 files (511 posts), 188.5MB
Queued: 188.5MB
[01]
[02]
[03]
[04]
[05]
[06]
[07]
[08]
[09]
[10]
[Total] 0.0KB/s, 188 MB queued, ETA: 00:00:00

And here is the logfile for this:

2008-05-04 00:36:34,779 INFO 
2008-05-04 00:36:34,781 INFO hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
2008-05-04 00:36:34,890 LOGFILE (giganews) Opening 10 connections...
2008-05-04 00:36:34,943 INFO hellanzb - Now monitoring queue...
2008-05-04 00:36:35,047 INFO Found new nzb (msgid: 3037325): McHale's Navy - 3x03 - It's a Mad, Mad, Mad War
2008-05-04 00:36:35,049 INFO Resuming: McHale's Navy - 3x02 - Lester, the Skipper
2008-05-04 00:36:35,109 INFO Parsing: 3037326_McHale's Navy - 3x02 - Lester, the Skipper.nzb...
2008-05-04 00:36:35,292 INFO Parsed: 16 files (511 posts), 188.5MB
2008-05-04 00:36:35,343 INFO Queued: 188.5MB

Any suggestions?

Pablo

Seems as though hellanzb is working fine but is having trouble with either your gignews account or with finding the files you want to download on giganews.  Stop hellanzb then delete the "lester the skipper.nzb" from daemon_current (or daemon_working - I'm at work and can't check which directory it is) and it should start processing the Mad mad war one when it next starts up.

---

### Post by Luke1972 on 2008-05-13
> **gedekran said:**
> How does one get hellanzb to process zipped nzb files?

I tried searching, played around with the conf file, read every page of this thread and still haven't figured it out.

Found this section in the conf file, but not sure how to configure it to process zipped nzb files.


```
# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
Hellanzb.NZB_ZIPS = '.nzb.zip'
```

Thanks.

Not tried this myself but isn't that telling you the zipfile the nzbs are in must be named "*.nzb.zip" for them to be processed in the daemon.queue directory?  Can you confirm you've tried that?

---

### Post by marcus2004 on 2008-05-17
Sorry for jumping in but I thought that this might be useful here. I was having an issue with hellanzb not being able to download with nzb's from tvnzb site. If anyone else is having this trouble there is a ticket:

[http://www.hellanzb.com/trac/hellanzb/ticket/390](http://www.hellanzb.com/trac/hellanzb/ticket/390)
And the fix is below. I think it comes do to the way hellanzb handles multiple groups that are listed in the nzb. 
You have to redownload hellanzb and make the changes bellow and then run
 sudo python setup.py install

To make the change follow these steps:
Changed section in NZBParser.py (and recompiled) ORIGINAL:

Orginal:

  elif name == 'group':
            newsgroup = self.parseUnicode(''.join(self.chars))
            self.file.groups.append(newsgroup)


CHANGED:


  elif name == 'group':
            newsgroup = self.parseUnicode(''.join(self.chars))
            self.file.groups = newsgroup

Hope this can help someone else.

---

### Post by Coollie on 2008-05-17
Hi all,

I've manage to get hellanzb to work. No problems there. I want to use hellahella as an web interface so I can manage it all, but I'm having lots of trouble with it. 

After installation (as [described]("http://hellanzb.com/trac/hellanzb/wiki/HellaHella")), still can't get it to work. After looking closely at the errors I went on an adventure and tried to solve the problem with no succes. See attached files for errors. File 1 are errors after fres install. File 2 are errors after I've changed the file mentioned in the error file 1.

Is there anyone who has installed hellahella with no problems?

GreetZ!

---

### Post by gsmaverick on 2008-05-29
I am also getting the daemonize error, can't find it, and i have latest packages of everything.

---

### Post by tododo on 2008-05-31
Hi all

Complete noob here so please go easy

Just installed hellanzb and all working fine via the command line method ....pretty chuffed thanks guys

Now looking to get hellaworld installed so I can get a nice gui to play with 

Ive installed php, mysql etc but really dont know what to do next

Has anybody got any experience of setting this up ......if somebody has time would they mind doing a complete guide step by step

Ill keep trying to figure it out in the meantime

Thanks again

---

### Post by Jungleboss on 2008-06-01
Have anyone got Hellahella to work under Hardy?

---

### Post by ukdeveloper on 2008-06-10
Hi, i am trying to use your hellanzb.sh script

Get through stage 1 ok, then halfway through stage 2 I get this error:

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up build-essential (11.1) ...
2/3 - compiling yenc, please standby
/home/hellanzb.sh: line 84: wget: command not found
tar: yenc-0.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/hellanzb.sh: line 86: cd: yenc-0.3: No such file or directory
python: can't open file 'setup.py': [Errno 2] No such file or directory
python: can't open file 'setup.py': [Errno 2] No such file or directory
3/3- removing temporary files, please standby
rm: cannot remove `yenc-0.3.tar.gz': No such file or directory
script finished, exiting now
root@hellanzb:~#

Now im stuck lol, and in VERY new to linux (ubuntu)

any pointers?

Thanks, Carl.

---

### Post by PeteZA on 2008-06-10
So I have been using hellanzb now for quite a while with the hella screenlet. Works like a charm, love it, however every now and then my downloads disappear. I am not sure how to even look for the logs so any help would be appreciated

---

### Post by Jungleboss on 2008-06-16
For instructions how to install **Hellahella** under Hardy please check this thread out:

[http://ubuntuforums.org/showthread.php?t=770166](http://ubuntuforums.org/showthread.php?t=770166)

Some applications that requires Python 2.5 may stop working though.

---

### Post by geezerone on 2008-06-29
Just stumbled across this thread and didn't realise nzb files could be downloaded in *nix so glad to see it can and not rely on Windows!

I installed hellanzb via synaptic but where and how is it run. Any tips on GUI too for it?

TIA

---

### Post by bvanaerde on 2008-06-30
@geezerone: Please read the first post of this topic. Nr. 9 will tell you how to run the program.
And check Jungleboss' post for a GUI ;)

---

### Post by geezerone on 2008-06-30
Found nice and easy to install gui from a post _**[here]("http://ubuntuforums.org/showthread.php?t=708248&highlight=hellagui")** _called _**[lottaNZB]("http://www.lottanzb.org/")**_.

I uninstalled from Synaptic and manually installed hellanzb (after downloading [version 0.13]("http://www.hellanzb.com/distfiles/hellanzb-0.13.tar.gz") and not 0.9) and now working. :D

---

### Post by bvanaerde on 2008-07-01
Thanks for sharing! Seems to be a bit easier than Hellahella, imo.

---

### Post by nhasian on 2008-07-01
i've been running hellanzb just fine until yesterday.  It simply stopped downloading files.  I'm thinking one of those automatic ubuntu updates clobbered hellanzb.  anyone else having this problem?  how can i see what packages were recently installed and if it changed anything hellanzb needs to run (ie python)

---

### Post by geezerone on 2008-07-01
> **bvanaerde said:**
> Thanks for sharing! Seems to be a bit easier than Hellahella, imo.

No problem!

The latest version of Lotta is now out (0.3) and the installer for Ubuntu is a simple click and go. I watched the install and it downloads dependencies and hellanzb automatically too! :KS - a does everything solution for many I'm sure.

---

### Post by tododo on 2008-07-07
Hi all

I hope somebody can help.....Ive got hellanzb running fine.....also managed to get hellaworld set up as a gui frontend

I have a slight problem in that when files are downloaded and go to a named folder the file that is created by hellanzb is unreadable

I have to keep changing permissions for the folder to get into the file

Anybody have any ideas
Thanks for any advise

---

### Post by chalewa on 2008-07-07
> **tododo said:**
> Hi all

I hope somebody can help.....Ive got hellanzb running fine.....also managed to get hellaworld set up as a gui frontend

I have a slight problem in that when files are downloaded and go to a named folder the file that is created by hellanzb is unreadable

I have to keep changing permissions for the folder to get into the file

Anybody have any ideas
Thanks for any advise

can you post your hellanzb.conf file? take out your username/pass obviously

---

### Post by tododo on 2008-07-14
> **chalewa said:**
> can you post your hellanzb.conf file? take out your username/pass obviously


Thanks.....Ive got hellanzb running as a daemon.....I think it may be something to do with the netmask section but not 100%

Thanks

---

### Post by chalewa on 2008-07-14
Hellanzb.DEST_DIR = '/home/griffithsl/Linux_Shares/Finished_Newsgroup_Downloads/'

so when they go there you can't access them? 

do you get the final file that you should be from the newsgroups? like an avi if you are downloading a movie?

---

### Post by tododo on 2008-07-14
Yes the file go in there fine howvever before I can view them I have to chmod the folder to get in there

---

### Post by chalewa on 2008-07-15
that's really strange, i don't know why you wouldn't have permission to access something that is being written to your home folder. 

do the permissions of the folder change after a restart? or when are the permissions changing?

---

### Post by tododo on 2008-07-16
> **chalewa said:**
> that's really strange, i don't know why you wouldn't have permission to access something that is being written to your home folder. 

do the permissions of the folder change after a restart? or when are the permissions changing?

It might be something to do with the fact that the folder is also smb share.....im going to play around with the smb.conf and see what happens

---

### Post by chalewa on 2008-07-16
> **tododo said:**
> It might be something to do with the fact that the folder is also smb share.....im going to play around with the smb.conf and see what happens

i don't see why that would be, and my equivilent folder is also a samba share, and i have none of these issues.

---

### Post by tododo on 2008-07-17
No matter what I try the files that hellanzb creates on my samba share are unreadable unless I chmod the folder first

I run everything through command line remotely if that makes a diffence and access everything through vista

I can create and delete files in the samba shares no problem through windows vista however whenever hellanzb finishes a download and puts the folder in the samba share I cant access

Any ideas??

Ive attached the smb.conf if that helps
Thanks again

When I check the permissions of the file or directory that hellanzb creates its like the following

griffithsl@griffithslubuntu-desktop:~/Linux_Shares/Finished_Newsgroup_Downloads$ ls -l
total 4
d--------- 2 root root 4096 2008-07-17 18:54 

Therefore I cant do anything with the folder......does it have something to do with the fact that to run hellanzb I have to use sudo???

Sorry bit of a newbie

---

### Post by chalewa on 2008-07-17
what happens if you change your security to share?

what happens if you try to share your 'done' folder specifically?

---

### Post by tododo on 2008-07-19
> **chalewa said:**
> what happens if you change your security to share?

what happens if you try to share your 'done' folder specifically?

tried both those options but still the file that is created has locked down permissions

Annoying

These are the groups griffithsl belongs too
griffithsl@griffithslubuntu-desktop:~/Linux_Shares/Finished_Newsgroup_Downloads$ groups
griffithsl adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare

---

### Post by tododo on 2008-07-23
Does anybody have any ideas....im really stuk

Does is matter that i have to run sudo for hellanzb to work??

Running out of ideas

---

### Post by geezerone on 2008-07-23
Have you tried LottaNZB (see my Signature for link) which installs Hella and a nice GUI too very simply?

---

### Post by tododo on 2008-07-24
Finally sorted it....reinstalled everything and instead installed hellanzb from the repositories

All now working as it should

Chuffed

Thanks for the advise all

---

### Post by Drizzel on 2008-08-08
Well I just installed hellanzb via synaptic. How do I configure it? Isnt there a way to control hellanzb through firefox. Like some kind of localhost:8080 or something? I'm lost here. I dont want to install lottanzb as its lacking a lot of features. I need to set my server stuff and enable ssl. Why is there no documentation on how to actually run hellanzb on their site?

This is the most difficult thing to use ever. Something as simple as downloading nzbs shouldnt be so hard to get going. I edited everything in the hellanzb.conf file.. set my server stuff, set ssl to true etc and it still wont connect. Worthless. I dont know how so many people use this app.

I have everything set now in the conf file. I have compared it to someone else's working config file and everything is right, but it still wont connect. I decided to hell with it and killed the hellanzb daemon. Now I'm using lottanzb as standalone and everything works great.. SSL and all. So the big question is why doesnt hellanzb work for me?

---

### Post by BassKozz on 2008-08-15
Is there a way to force hellanzb to rename the files & directories that use NON-SAMBA-FRIENDLY characters?

For example, if a file or directory has a colon or question mark ( : ? ) in it it will show up on my XBMC box all garbled.
i.e. Ubuntu:Hardy = usdgfst54~43 (or something to that extent)

---

### Post by at0mic on 2008-09-07
when i try to download something it goes at 9KB/sec as if theres something wrong with the connection and the data is only for trying to connect... yet i can connect and dl at over 1MB /sec with klibido... how can i find out what is going on with the 0 transfer when there is no noticable issue on the front end?

---

### Post by at0mic on 2008-09-07
figured out my own problem. had to do with the source nzb and how hella handled it. anotehr poster posted about it.

---

### Post by Pastortom on 2008-09-24
Quick question..

Im using Hellanzb and Lottanzb with unrar and Ive got some issues..

Sometimes when I download 350meg videofiles they dont unrar automatically, and sometimes if they do I just get a folder with the name of the videofile with NO contents.. and if I try to look for the rar files in hellanzb's folder theyre gone.. 

Its really really frustrating.. as it happens only sometimes with some files.. 

I figured it might have something to do with "par's" needed, and that the rar files were corrupt, so I removed "Only download par's when necessary" and it seemed like it fixed the problem with the next .nzb's.. but again today I downloaded 5 350meg videofiles, and only 2 of the successfully unpacked, the 3 others I had to download with torrent since I didnt wanna bother anymore! :(

I really like Lottanzb, its so easy and fun when it actually works, but its a pain in the *** when it doesnt work, and you cant fix it as easily as you could with Newsleecher or any other usenet application for windows.. 

Help?!

---

### Post by BassKozz on 2008-09-24
> **Pastortom said:**
> Quick question..

Im using Hellanzb and Lottanzb with unrar and Ive got some issues..

Sometimes when I download 350meg videofiles they dont unrar automatically, and sometimes if they do I just get a folder with the name of the videofile with NO contents.. and if I try to look for the rar files in hellanzb's folder theyre gone.. 

Its really really frustrating.. as it happens only sometimes with some files.. 

I figured it might have something to do with "par's" needed, and that the rar files were corrupt, so I removed "Only download par's when necessary" and it seemed like it fixed the problem with the next .nzb's.. but again today I downloaded 5 350meg videofiles, and only 2 of the successfully unpacked, the 3 others I had to download with torrent since I didnt wanna bother anymore! :(

I really like Lottanzb, its so easy and fun when it actually works, but its a pain in the *** when it doesnt work, and you cant fix it as easily as you could with Newsleecher or any other usenet application for windows.. 

Help?!

How old are the nzb's your downloading?
Where are you obtaining these nzb's (i.e. NZB distribution site)?
Who is your usenet provider? or are you using your ISP to provide usenet access?

My guess is (and this is from experience) that the NZB's that you are using point to (at least some, if not all) Usenet posts/files that are too old for your usenet provider to obtain and hellanzb fails to fix using par's since there isn't enough data available to uncompress/decrypt the post.

**Solution**: Get yourself a solid usenet provider (especially if your trying to use your ISP's service) like: Giganews.com or NewsHosting.com
and/or
Use NZB's that are more recent (less then 60days old is a good start).

---

### Post by Pastortom on 2008-09-24
> **BassKozz said:**
> How old are the nzb's your downloading?
Where are you obtaining these nzb's (i.e. NZB distribution site)?
Who is your usenet provider? or are you using your ISP to provide usenet access?

My guess is (and this is from experience) that the NZB's that you are using point to (at least some, if not all) Usenet posts/files that are too old for your usenet provider to obtain and hellanzb fails to fix using par's since there isn't enough data available to uncompress/decrypt the post.

**Solution**: Get yourself a solid usenet provider (especially if your trying to use your ISP's service) like: Giganews.com or NewsHosting.com
and/or
Use NZB's that are more recent (less then 60days old is a good start).

Thanks for your reply,

but no to all your questions..

Ive been downloading usenet files for the last 2 years, and I know very well how the system works with the days old, par'ing, etc etc..

and this is not the issue..

usenet provider: newshosting.com
nzb base: newzbin.com

The files Im downloading are files released within the last 24 hours.. 

and if I stop lottanzb during processing I can unrar the file and play it with VLC player totally fine as a video file, if I let Lottanzb/Hellanzb continue it deletes the rar files cause it "thinks" it has unpacked them, but infact theres only a folder with the videofiles name, nothing in it..

This happens in 3/5 attempts.. the 2 other attempts it manages to unpack the videofile, and I get a smile on my face..

How to fix this permanently? Considering Im using an uptodate usenet provider and nzb's released within the last 24 hours.. (in other words 100% bonifide working downloads that WOULD unpack totally fine in Windows with Newsleecher)

---

### Post by Pastortom on 2008-09-25
anyone?

bump!

---

### Post by BassKozz on 2008-09-25
Pastortom,

I am not using lottanzb, I simply installed [hellanzb]("http://www.hellanzb.com/") and I use [hellahella]("http://www.hellanzb.com/trac/wiki/HellaHella") as my webGUI in addition to [hellafox]("https://addons.mozilla.org/en-US/firefox/addon/6230") to download NZB's (newzbin.com).  But I assume Lottanzb simply installs hellanzb for you, so I would check for ***[COLOR="Red"]/var/tmp/hellanzb.log[/COLOR]*** and see if you can figure out whats going on. Further more you can modify ***[COLOR="Red"]/usr/etc/hellanzb.conf[/COLOR]*** and turn on debugging log and then check the log file ***[COLOR="Red"]/var/tmp/hellanzb-debug.log[/COLOR]***.
You might also want to post the contents of these log files here, just make sure to use the **[COLOR="Blue"][code][/COLOR]** tags.
HTH,
-BassKozz

---

### Post by geezerone on 2008-09-27
Is there a way to configure LottaNZB to automatically open a .nzb file as the option on my machine is to save file. Then I have to open LottaNZB and add the file manually for it to work. 

I have browsed for /usr/bin/lottanzb as the application to open .nzb files which just opens LottaNZB BUT doesn't add the .nzb file.

Any ideas?

---

### Post by MannyBoy on 2008-10-02
Anybody know why it unrars after my download is complete?
My settings are
# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = True

So why is it still unraring?
This is what typically happens:

Transferred ##MB in #s at ####KB/s (file)
Veryifing via par group: xxx
Finished par verify
Unraring xxx.rar
Finished unraring
Finished processing

Any help would be great.

---

### Post by bvanaerde on 2008-10-04
Mannyboy, change
> #Hellanzb.SKIP_UNRAR = True
to
> Hellanzb.SKIP_UNRAR = True
In other words: uncomment that line.

---

### Post by MannyBoy on 2008-10-04
Awesome it worked! Thanks alot! :D

---

### Post by ernst320 on 2008-11-28
Hi Everyone,

I am new to Linux, trying to follow this guide to install hellanzb.  I got to step #9 (running the program) and I got this error:

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize



Can someone please help me with this?

Thanks

---

### Post by ernst320 on 2008-11-28
I am having the same error message.  Did you ever find a solution for this problem?

---

### Post by TokenBad on 2008-11-29
ok I installed hellanzb through sudo apt-get install hellanzb but when try to run it get this:

/hellanzb-0.9$ ./hellanzb.py
Traceback (most recent call last):
  File "./hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/home/tokenbad/hellanzb-0.9/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/home/tokenbad/hellanzb-0.9/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

any help?

TokenBad

---

### Post by BassKozz on 2008-12-17
> **ernst320 said:**
> Hi Everyone,

I am new to Linux, trying to follow this guide to install hellanzb.  I got to step #9 (running the program) and I got this error:

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize



Can someone please help me with this?

Thanks

> **ernst320 said:**
> I am having the same error message.  Did you ever find a solution for this problem?

> **TokenBad said:**
> ok I installed hellanzb through sudo apt-get install hellanzb but when try to run it get this:

/hellanzb-0.9$ ./hellanzb.py
Traceback (most recent call last):
  File "./hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/home/tokenbad/hellanzb-0.9/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/home/tokenbad/hellanzb-0.9/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

any help?

TokenBad
HellaHella doesn't work with Python 2.5 :(
See: [http://www.hellanzb.com/trac/hellanzb/ticket/412](http://www.hellanzb.com/trac/hellanzb/ticket/412)

---

### Post by TokenBad on 2008-12-17
Thats ok..I found newsleecher and it works good...

TokenBad

---

### Post by tiberious- on 2008-12-17
> **at0mic said:**
> when i try to download something it goes at 9KB/sec as if theres something wrong with the connection and the data is only for trying to connect... yet i can connect and dl at over 1MB /sec with klibido... how can i find out what is going on with the 0 transfer when there is no noticable issue on the front end?

in the hellanzb.conf file set skipGroupCmd = True

@ernst320,TokenBad: Looks like you are trying to run version 0.9 still, get the latest from the official repositories and run hellanzb.py from a location other than previously installed (so not in hellanzb-0.9 folder

---

### Post by BassKozz on 2008-12-17
> **BassKozz said:**
> HellaHella doesn't work with Python 2.5 :(
See: [http://www.hellanzb.com/trac/hellanzb/ticket/412](http://www.hellanzb.com/trac/hellanzb/ticket/412)

Fixed!!!
Simply issue: ```
sudo easy_install -v "Myghty==dev,>=1.1.1dev-r2155" 
```
Thanks pjenvey :D

---

### Post by RaZoR1394 on 2008-12-22
I have been a longtime user of hellanzb but I wanted to try something new so I went for sabnzbd directly from launchpad repository.

[http://forums.sabnzbd.org/index.php?topic=387.0](http://forums.sabnzbd.org/index.php?topic=387.0)

For a longtime (longer than hellanzb) user of Torrentflux-b4rt It's more appealing.

Last upstream update of hellanzb was March 2007. And personally I have encountered some annoying bugs.

Try it, you may like it.

---

### Post by Pilo on 2009-03-07
I've seen a couple of other init scripts floating around to run hellanzb as in daemon mode on startup, but I made this one so I thought I'd share:
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:             hellanzb
# Required-Start:       $local_fs $remote_fs $network
# Required-Stop:        $local_fs $remote_fs $network
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Short-Description:    Start hellanzb daemon
### END INIT INFO
#
# hellanzb       Start the hellanzb.
#


set -e

PATH=/bin:/usr/bin:/sbin:/usr/sbin
DESC="hellanzb downloader"
NAME="hellanzb"
DAEMON=/usr/bin/hellanzb
DAEMON_OPTS="-D"
SCRIPTNAME=/etc/init.d/$NAME
USER=pilo

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

. /lib/lsb/init-functions

#
#	Function that starts the daemon/service.
#
d_start() {
	log_daemon_msg "Starting $NAME"
    if start-stop-daemon --start --quiet --user $USER \
        --chuid $USER:$USER --exec $DAEMON -- $DAEMON_OPTS; then
		log_end_msg 0
	else
		log_end_msg 1
	fi
}

#
#	Function that stops the daemon/service.
#
d_stop() {
	log_daemon_msg "Stopping $NAME"
    if start-stop-daemon --stop --quiet --retry 5 --user $USER \
        --name $NAME; then
		log_end_msg 0
	else
		log_end_msg 1
	fi
}

case "$1" in
  start)
    d_start
    ;;

  stop)
    d_stop
    ;;
  
  restart|force-reload)
    d_stop
    sleep 3
    d_start
    ;;

  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0

```

---

### Post by bvanaerde on 2009-03-07
> **RaZoR1394 said:**
> SABnzbd+
[http://forums.sabnzbd.org/index.php?topic=387.0](http://forums.sabnzbd.org/index.php?topic=387.0)
Try it, you may like it.

I tried, and I liked :D
I can recommend this to anyone searching for a good hellanzb alternative! The web GUI is great!

---

### Post by marklid on 2009-03-07
I tried sabnzb for a while but had a lot of downloads 'fail' for some reason, went back to Hellanzb and had no probs.

---

### Post by Darth_Mueller on 2009-03-14
hellanzb worked now for over a half year without problems, but since yesterday, randomly after a download the work dir is deleted(usually only the files inside should be deleted after its complete)
Does anyone have a clue what can cause that?

---

### Post by penduleum on 2009-03-21
hey.

I have installed hellanzb, but get the following error:

```
Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize

```

I tryed the sellution from one poster:

CODE]sudo easy_install -v "Myghty==dev,>=1.1.1dev-r2155"[/CODE]

and got the following error:

```
sudo: easy_install: command not found
```

I ame not shure if its ment to be to use the command easy_install (is it a command???)

How can i fix this?
if this is fixend, then i can remove permantly xp from my box....
thx

edit:

found the sollution!!!
You need to use hellanzb-0.13, then you dont have the problem i mentioned.

When you have a error that you cant create a directory in some disks, then use sudo hellanzb instead of hellanzb.
laterz

---

### Post by Tobas on 2009-03-27
I just want to say that i love hellanzb, im working almost 2 years with it and it doesnt stop working.
I have just 1 question in fine tuning my Hellanzb, i hope it can be done.

Situation --> folder full of folders (apps,movies,music not organised)
what i want --> folder with sub-folders apps, movies, music and in that foldes the folders with content.
Is there a way to put a nzb in the nzb folder like : MOVIE_blablamovie.nzb that this "blablamovie" will be unpacked in /home/tobas/media/movie instead off in /home/tobas/media
and the same for APPS_blablaapps.nzb and MUSIC_blablamusic.nzb 

I hope someone knows.

Tobas

---

### Post by BassKozz on 2009-03-27
Tobas,

For one I know if you use newzbin.com hellanzb automatically creates folders based upon the subsection the nzb file is in. 

For Example: If you download an NZB from newzbin.com that is in the Movies category, hellanzb automatically unpacks the download into a "Movies" folder (it will create the folder automatically if it doesn't already exist).

You gotta love hellanzb+newzbin :-D

On the flip side if you create your own NZB by doing a RAW usenet search on newzbin.com hellanzb does NOT place the files/folder into a category even if the category is selected in your search.

For example: do a "Usenet (raw)" search on hellanzb in the TV category and package a nzb and download it will unpack into */media/ instead of */media/tv.

So for a quick fix you could always use newzbin.com reported nzb's for your downloads and that would automatically sort for you, and you would have to manually sort/move the raw search downloads.

I am sure there is a way to tie into that function of hellanzb to do what it is your looking for but my python skills are slim to none (leaning more towards none :P ), I would recommend requesting a feature request on hellanzb's trac: [http://www.hellanzb.com/trac/hellanzb/newticket](http://www.hellanzb.com/trac/hellanzb/newticket)
You have to login first using guest/guest (user/pass) and then submit your ticket. Unfortunately account creation is turned off for hellanzb do to spam related issues IIRC, but there is already a [recommendation to switch to LaunchPad]("http://www.hellanzb.com/trac/hellanzb/ticket/419#comment:2"), let's see if it happens, I for one would welcome a change from trac to LaunchPad.  Anyways I got way off trac (pun intended) here...

HTH,
-BassKozz

---

### Post by keypox on 2009-03-29
Hey i got this intalled and edited the config file. I run program in terminal and it just doesnt download.  Dunno if it has errors or anyting it doesnt say anything.

Hsudo gedit /usr/etc/hellanzb.conf
here is what i used 

then run hellanzb.py

I get 

Starting queue daemon
(astra) Opening 8 connections...
hellanzb - Now monitoring queue...
Resuming: this


but it doesnt do anything.

---

### Post by BassKozz on 2009-03-29
keypox,
Check to make sure your Usenet provider (astra) credentials are entered correctly in conf. Also did you download a NZB for hellanzb to use ("Resuming: this", what is this)?

---

### Post by keypox on 2009-03-29
> **BassKozz said:**
> keypox,
Check to make sure your Usenet provider (astra) credentials are entered correctly in conf. Also did you download a NZB for hellanzb to use ("Resuming: this", what is this)?

I have checked and doubled checked and will recheck now.  

This is the name of the nzb file.  I changed the name for privacy... hehe

Here is what i am doing to check conf

sudo gedit /usr/etc/hellanzb.conf
(is this the correct one)

And these are the settings i changed

(id = 'astra',
             hosts = [ 'ssl-us.astraweb.com:443' ],
             #hosts = [ 'news.changeme.com:119', 'morenews.changeme.com:119' ],
             username = 'nonya',
             password = 'business',
             connections = 8,
             antiIdle = 7 * 60,          # 7 minutes
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #maxSpeed = 150             # limit to 150kB/s
             )

# Important locations
Hellanzb.PREFIX_DIR = '/home/keypox/'

I take it when there is a # it is not being called right?

Im thinking i need to uninstall and start over.   Ilike the idea of this thing though.

---

### Post by BassKozz on 2009-03-29
> **keypox said:**
> 
Here is what i am doing to check conf

sudo gedit /usr/etc/hellanzb.conf
(is this the correct one)
Yes

I think I see what's wrong, your trying to use SSL but you haven't got it enabled in the conf file...
Try this:
```

defineServer(id = 'astra',
             hosts = [ 'ssl-us.astraweb.com:443' ],
             username = 'nonya',
             password = 'business',
             connections = 8,
             antiIdle = 0,
             ssl = True
             )
```

---

### Post by keypox on 2009-03-29
eyah i thought that it might not support SSL so i also tried the non ssl same resutls

Starting queue daemon
(astra) Opening 8 connections...
hellanzb - Now monitoring queue...
Resuming: linux

thats all i get... pan is working but not quite as nice as this.

Just found [http://www.lottanzb.org/](http://www.lottanzb.org/) looks very very promising uses hellanzb but has a nice gui front end... trying now :)

Damnit still not working :(

---

### Post by keypox on 2009-03-29
ok your really prob gonna laugh at what hte problem was...

i was using 0.5 version because i thought that 0.5 > 0.13 ... hehe

i bet all will work now

yeah it seems to be workign now :) hehe

but i really like the lattaNZB gui.  Also it will install everything for you too. 

Also i cannot run hallanzb from terminal because i get this error. 

hellanzb v0.13 (config = /usr/etc/hellanzb.conf, C yenc module)
Exiting: FatalError'>: Required directory not defined in config file: Hellanzb.POSTPONED_DIR

---

### Post by keypox on 2009-03-30
i think i fixed it by coping the new cfg file that lottanzb made.  
I like the gui but maybe not all the time ;)

---

### Post by Bultot on 2009-04-25
With Jaunty, the daemon script isn't working anymore.
I'm looking for a fix.

---

### Post by jmikola on 2009-05-02
> **Bultot said:**
> With Jaunty, the daemon script isn't working anymore.
I'm looking for a fix.

I just upgrade to Jaunty this evening and noticed the same.  I was using the hellanzb/hellahella init script that was posted many pages back in this thread.  I replaced it with Pilo's script, which he posted earlier on this page (#370), and it appears to work fine.

Not sure what the difference between both init scripts is, but since I no longer have need for hellahella, Pilo's script was an ideal solution.

---

### Post by shadowlands on 2009-05-25
Hello, thanks to the folk who posted this.  However I am not understanding how steps 8-10.  Can some one please help me with very simple step by step wording?  Thanks in advance.

---

### Post by mbutash on 2009-05-28
Hi, was just curious if anyone else experiences issues with hellanzb on jaunty.  It seems unrar functions don't work, logs only indicated generically that unrar fails on any file it downloads.  I tried "unrar" as well as "unrar-free", neither works.  I'm thinking hellanzb isn't calling it correctly or something.  All in all, I've really had nothing but issues with hella hanging on downloads, not cleaning up after itself, and other buggy issues.  Not terribly impressed...  2009-05-26 08:15:25,870 ERROR generic-file: A problem occurred: FatalError'>: There was a problem during unrar, output:  unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers   Extracting from /var/usenetnzb/daemon.processing/generic-file/generic-file.rar  Extracting  generic-file.iso                                          Failed     1 Failed 2009-05-26 11:41:39,020 INFO

---

### Post by nhasian on 2009-05-28
I have three computers that run hellanzb fine in Jaunty 9.04.  Alternatively you can try SABnzbd

[http://www.sabnzbd.org/](http://www.sabnzbd.org/)



> **mbutash said:**
> Hi, was just curious if anyone else experiences issues with hellanzb on jaunty. 

---

### Post by musta78 on 2009-06-10
My browsing computer is windows based.  But my server where I have installed hellanzb is ubuntu.  

What I want is that firefox sends nzb files directly to nzb folder on my server.  Is there a way to do this when using windows?

---

### Post by lowph on 2009-06-10
If you're using newzbin then you might want to try Hellafox, a simple Firefox extension to download and start a nzb download directly from newzbin. Works fine on both windows and linux.

---

### Post by BassKozz on 2009-06-11
> **musta78 said:**
> My browsing computer is windows based.  But my server where I have installed hellanzb is ubuntu.  

What I want is that firefox sends nzb files directly to nzb folder on my server.  Is there a way to do this when using windows?

Checkout this add-on for firefox: [https://addons.mozilla.org/en-US/firefox/addon/6230](https://addons.mozilla.org/en-US/firefox/addon/6230)

---

### Post by theluddite on 2009-06-21
> **mbutash said:**
> Hi, was just curious if anyone else experiences issues with hellanzb on jaunty.  It seems unrar functions don't work, logs only indicated generically that unrar fails on any file it downloads.  I tried "unrar" as well as "unrar-free", neither works.  I'm thinking hellanzb isn't calling it correctly or something.  All in all, I've really had nothing but issues with hella hanging on downloads, not cleaning up after itself, and other buggy issues.  Not terribly impressed...  2009-05-26 08:15:25,870 ERROR generic-file: A problem occurred: FatalError'>: There was a problem during unrar, output:  unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers   Extracting from /var/usenetnzb/daemon.processing/generic-file/generic-file.rar  Extracting  generic-file.iso                                          Failed     1 Failed 2009-05-26 11:41:39,020 INFO

I think this is a problem with unrar not jaunty.  I've experienced a simliar problem recently as detailed here:

[http://ubuntuforums.org/showthread.php?t=1187729&highlight=unrar+libstdc](http://ubuntuforums.org/showthread.php?t=1187729&highlight=unrar+libstdc)

Is anyone else finding that unrar is not extracting files correctly?

---

### Post by musta78 on 2010-01-14
Hello all!

I messed up my backup "hellanzb.conf" and now I'm stuck with nothing.  

Even when I try uninstalling it and install it back the file is still messed up.

Could someone plz help me and post a "fresh" conf file?  I only need what a copy of the text inside.

Thanxs!

---

### Post by mpm on 2010-01-14
Here it is, good luck.

# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 1057 2007-03-27 04:13:53Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'changeme',
             hosts = [ 'news.changeme.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'changeme',
             password = 'hella',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = '/ext2/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'usenet/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True


# Maximum amount of memory used to cache encoded Article data segments.
# hellanzb will write article data to disk when this cache is exceeded
# Available settings:
# -1: Unlimited size
#  0: Disable cache (only cache to disk)
# >0: Limit cache to this size, in bytes, KB, MB, e.g.:
#     1024 '1024KB' '100MB' '1GB'
#Hellanzb.CACHE_LIMIT = 0


# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
#Hellanzb.PAR2_CMD = None

# Skip unraring during post processing
#Hellanzb.SKIP_UNRAR = False

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Disable ANSI color codes in the main screen (preserves the in place scroller)
#Hellanzb.DISABLE_COLORS = False

# Disable ALL ANSI color codes in the main screen (for terminals that don't
# support ANY ANSI codes
#Hellanzb.DISABLE_ANSI = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'

---

### Post by musta78 on 2010-01-31
I've got this beutiful little program up and running!  I love it, saves med a lot of time:)

Only one thing that is a bit annoying.  When the files a prosecesed and ready there seems to be a sample file a lot of the times.  

Is there a way to automaticly delete all sample files?  I really don't need 2 min sample when I got everything I wont right next to it:)

---

### Post by SilverWave on 2010-02-04
eh guys? You may want to look at sabnzbdplus it beats hellananzb out of the park.
#
All the dependencies are installed by default once you select:

sabnzbdplus

You may also want to install these themes and see which you like the best.

sabnzbdplus-theme-iphone
sabnzbdplus-theme-plush
sabnzbdplus-theme-smpl

Its got real bandwidth limiting and schedules (so you can work around traffic shaping).

> SABnzbd+ is a web-based binary newsgrabber written in Python, with support for
the popular nzb file format. It greatly simplifies the process of downloading
from usenet, thanks to a friendly web-based, fully customizable user interface
and advanced built-in post-processing options including the ability to
automatically verify, repair, extract and clean up downloaded posts.

Multiple servers are supported, as well as secure (ssl) connections, ipv6,
scheduling, pausing and resuming downloads, queue manipulation, rss feeds,
newzbin integration, automatic sorting, a download history, email
notifications, and custom post-processing scripts.

The program is a fork of the original SABnzbd code, which is no longer actively
developed.

---

### Post by theluddite on 2010-02-10
> **SilverWave said:**
> eh guys? You may want to look at sabnzbdplus it beats hellananzb out of the park.


Thanks for the suggestion.  I was looking for an alternative since I started having trouble with hellaznb dependencies and hellafox.  I just installed sabnzbd a few hours ago and I'm already hooked.  It's way more configurable than hellanzb and I dig the rss feed.

---

### Post by odin23342 on 2012-04-04
Here are some  helpful things that i use all the time to  repair and extract files easily editable to fit your specific needs. I find it a lot faster then other methods. It will repair the files then  extract them. I am sure there are better ways to write them but  below is simple enough anyone could understand and edit them. 


cd to the directory or add the directly name after find( i just do my entire download directory.
```
find -type f -name '*.par2' -exec par2 r {} \; && find -type f -name '*.rar' -exec unrar x {} \;
```If you want to clean up everything after this is pretty handy.
```

rm *.r00 ; rm *.r0{1..9} ; rm *.r{10..100} ; rm *.rar ; rm *.srr ; rm *.sfv ; rm *.PAR2 ; rm '*.par2' ; rm *.par ; rm *.par2x ; rm *.nzb ; rm *.nfo
```If interested i can post the code to the shell script with those inside of it.

---

### Post by sam088 on 2012-04-05
Hi,
Thank you very much ,i have fallow all the steps and it successfully installed,now i can use it .
thanks.
-----------

[Debra Fine](http://www.ezdia.com/epad/debra-fine-books/4091/)

---

