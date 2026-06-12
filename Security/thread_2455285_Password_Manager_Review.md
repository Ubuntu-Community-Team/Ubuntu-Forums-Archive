---
title: "Password Manager Review"
date: 2020-12-16
forum: Security
---

### Post by llamabr on 2020-12-16
It's 2021, and it's finally time to do something about your passwords. A few years ago I wrote a short introduction to password managers, including an introduction to what they do, what they are, why you should definitely be using one, and which ones are available on Linux. My original post is here:
[https://ubuntuforums.org/showthread.php?t=2347796&p=13588049](https://ubuntuforums.org/showthread.php?t=2347796&p=13588049)
If you don't have a password manager, you definitely should. You can start small by just using one to store your banking information, or other logins you don't need every day, but which require strong password protection. Before long, you'll get your mind around it and you'll be using it for all your accounts.

My criteria for inclusion in the list is that it should be available on Linux and *bsd, that it would be nice if it were also available on other platforms (including MS Windows, Android, iOS, and MacOS), and that it should, but need not, sync with the cloud. You can review my notes about Password Gorilla, LastPass, KeePassX, and Encrpytr. Not included in that original list:

**[Lockwise]("https://www.mozilla.org/en-US/firefox/lockwise/")**: This is the default password manager included in Mozilla Firefox. If you "sync" your firefox accounts, you'll find that your passwords are also sync'd on the desktop. Lockwise is also available in the Android and iOS store. If you're using FF, you're probably using Lockwise, whether you know it or not. You can sync your mobile device with your desktop and access your passwords on any device.

For most regular people, [LastPass]("https://www.lastpass.com/how-lastpass-works") is a really good choice. It's free, easy to use, comes with a FF plugin, and has some notable premium features. 

However, at the time, I recommended Encryptr by SpiderOak. First, it's extremely simple; many other password managers are bloated with confusing or unnecessary features. Second, it syncs to the cloud using SpiderOak's strong end-to-end encryption. And third, it comes recommended by Edward Snowden. Unfortunately, come 2021, [SpiderOak will sunset the Encryptr project]("https://spideroak.com/encryptr/"). On their website, Encyptr recommends moving either to 1password or bitwarden, and has included simple scripts to export to either of those platforms. If you use Encryptr, you need to export your data.

As a replacement, I've finally decided to switch to [pass]("https://www.passwordstore.org/"), "*the standard Unit password manager*". Pass is an extremely light, easy to use, feature rich password manager that follows the unix philosophy: it does one thing well,  but also takes advantage of interoperability with a suite of unix tools. Passwords live inside a png encypted file, which live in your home directory. That's it. As the same time, there are a number of [community projects and extensions]("https://www.passwordstore.org/#extensions") for pass, including GUIs and Android and iOS apps.

Setting up pass is easy. After installing on your machine, run
```
$ gpg2 --full-gen-key
```
This will generate the gpg2 key. Unless you're on a very old machine, choose 4096. Set up your pass phrase. You must remember this pass phrase. It should be impossible to guess, but rememberable by you. You must remember this pass phrase. Don't forget it. OK?

Next run
```
$ pass init user@email
```
This will create the ~/.password-store directory. At this point, you can include git functionality by also running
```
$ pass git init
```
This will create a git repository in your ~/.password-store/.git/ directory. Git repositories allow for local cloning, push'ing, pull'ing, and version control of your password repo. It is very handy.

That's it. You're done. Now create a saved password with
```
$ pass insert google/username
```
pass will prompt you for your google password, and save it in your pass directory. You can save additional google passwords simply by
```
$ pass insert google/username2
```
In addition to those two google account passwords, let's also throw in a:
```
$ pass insert yahoo/username
```
See your full tree of passwords with a simple
```
$ pass
```
In the above example, it would look like this:

```

$ pass
Password Store
&#9500;&#9472;&#9472; google
&#9474;** &#9500;&#9472;&#9472; username
&#9474;** &#9492;&#9472;&#9472; usename2
&#9500;&#9472;&#9472; yahoo
&#9474;** &#9500;&#9472;&#9472; username

```

Retrieving your passwords from pass is just as simple. In the example above, type:
```
$ pass google/username
```
Notice that pass respects tab completion. Type in your gpg2 password (not your google password, obviously) to access the file, and it spits out your google password. What could be easier?

I keep my ~/.password-store dir in my home directory on a public facing web server, to which I have ssh access, and on which git is installed, meaning I can ssh in to run pass on the CLI. However, I can also access my passwords on my local machine. On the server, which is where my google password is stored, run:
```
$ gpg2 --export-secret-keys > secret-keys.gpg
```
Move the file secret-keys.gpg to your local machine 
```
$ scp secret-keys.gpg username@local.machine.ip:~/
``` 
and then on the local machine, run:
```
$ gpg2 --import ~/secret-keys.gpg
```
This imports your keys from the server to your local machine. Finally, on the local machine:
```
$ git clone remote.machine.ip:~/.password-store
```
Your .password-store is now locally saved. You can run pass commands as you normally would. Try it with the -c flag to copy your password right to the clipboard, rather than to stdout. And with git integration, you have version control, meaning you can look back at old passwords. I can also push local changes back to the server. And of course, git is fantastically feature rich, so check out these extended git examples to get your money's worth: [https://git.zx2c4.com/password-store/about/#EXTENDED%20GIT%20EXAMPLE](https://git.zx2c4.com/password-store/about/#EXTENDED%20GIT%20EXAMPLE)

For example, one very cool use is to now [use pass to credential your remote git repositories]("https://github.com/languitar/pass-git-helper") on, e.g., GH by defining mappings between hosts and fields in the password-store. The possibilities are literally endless: do one thing and do it well, integrating with a suite of available unix tools. 

I will not recommend that you read the man page for pass, since moderators on ubuntuforums get all butt hurt when I do that, but I wouldn't run the software with out it. If you do read the manual, you'll find any number of useful features and examples. 

Finally, as always, don't forget to [practice good gpg keypair hygiene!]("https://www.linuxbabe.com/security/a-practical-guide-to-gpg-part-1-generate-your-keypair")

---

### Post by TheFu on 2020-12-17
Ars Technica [https://arstechnica.com/tag/password-managers/](https://arstechnica.com/tag/password-managers/) - not a direct link to the article, sorry.
Wirecutter: [https://www.nytimes.com/wirecutter/reviews/best-password-managers/](https://www.nytimes.com/wirecutter/reviews/best-password-managers/)

Everyone has different needs for a password manager.  Mine are simple.
[LIST]
[*]Never put passwords or a passwd DB into the cloud. I'm always shocked when people think this is an option or even a good idea. Would you leave your car keys sitting on top of the car?  Git is fine. Github and similar services - nope.
[*]Never use a password manager tied to any cloudy service. I'm always shocked when people think this is an option or even a good idea. Your computer security must really suck if you believe that some free, cloudy, service will keep your passwords safe.  I mean - SRSLY?????!
[*]Never use the password safe in any browser. Browsers are already full of major bugs due to being overly complex.
[*]Never use any browser addon/plugin with a password manager. Browsers are already full of major bugs due to being overly complex.
[*]Needs to support Linux, Windows, Android - I don't care about OSX or BSD. YMMV.  Make a list.
[*]Should support at least 2 different U2F keys for 2FA. To my knowledge, no password manager does this. I have 3 U2F key devices and setup at least 2 with accounts to ensure the failure or loss of 1 doesn't lock me out.  Why wouldn't a password manager do the same?
[*]Should keep passwords not actively being displayed encrypted in memory. Most OSes have a way to dump the RAM for running processes. I did this a few years ago with KeePassX for fun. Yep, all the passwords were there, unencrypted if the program wasn't "locked".
[*]Should be F/LOSS, $0, not just free to use, but free to modify and share.
[*]Should be easy enough to use that an 80+ yr old grandma isn't confused.
[/LIST]

There are all sorts of opinions about passwords, managing them, and how long, unique, they should be.  
* [https://blog.jdpfu.com/2010/04/24/keepassx-password-manager](https://blog.jdpfu.com/2010/04/24/keepassx-password-manager) - 10 yrs ago. I currently use KeePassXC, which isn't perfect.
* [https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager) - not just for passwords.
* [https://blog.jdpfu.com/2015/10/21/real-world-fido-u2f-use](https://blog.jdpfu.com/2015/10/21/real-world-fido-u2f-use)  - U2F for 2FA

My rule of thumb for passwords is simple. If I can memorize it, then it isn't long enough or complex enough, unless it is one that I must type into a physical device to unlock THAT specific physical device.  For online accounts, I'm never going to type that password in, so why not make it 40+ random characters (or as long as the input field allows)?  I've never heard any good arguement against that. Sure, the crypto-math says we don't need more than 13, truly random, characters for a password, but humans are terrible at "random", so just give up on that.  Length can protect humans from ourselves.  Don't even let your brain think it can memorize a 55 random character password.  

Sometimes, I use random characters for the username too. I cannot tell you my username for any financial accounts. I don't know them.  Some banks have much too short limits for password lengths, so random for the username (which can usually be 35+ characters) doesn't hurt.

And while we are talking about online security, please don't use the same email account everywhere.  The email account for your bank shouldn't be the same as you use for facebook, instagraph, or any other accounts.  Most people need 4 email accounts:
[LIST]
[*]Personal/family
[*]Work
[*]Online purchases
[*]Banking/Financial institutions
[/LIST]
If the first 3 accounts are hacked, it really won't impact you much financially. Not a big deal. Plus, you'll use those first 3 a few to many, times every week. You might use the Bank/401k/Brokerage email once a month, if that often.  Keep them separate.

IMHO.

---

### Post by Ralph L on 2021-01-12
I have been following this thread and think I will follow the The Fu's advice, and install Keepassxc and use a Yubikey 5 NFC.  When I go to  the Keepassxc download site I see multiple methods of installation:  appimage, Official Ubuntu PPA, or Ubuntu Package.  I am running Xubuntu 18.04.  I am wondering which would be best to use.  I kind of like appimages, since they are usually the most up to date, but are there any security risks using appimages.  As far as I know appimages are just object code files that is usually made available to any user of my computer (my wife and I).  What if somebody broke into my computer.  Would an appimage be more vulnerable to some malware, that might be in a user account, than something stored under the admin user account??

Also, after looking at Yubikey and Keepassxc I could use some instructions for how to set these things up.  First question is "Do I need to download YubiKey Personalization Tool?  Also, what is slot 1 and slot 2, and how should they be used?  And what is "Challenge Response Mode" and what other modes are there?  Should I use Challenge Response and how does that work?  Finally, do any institutions such as banks support the Yubikey directly in such a way that my key goes directly from my Yubikey to the bank without having to stop off in Firefox where The Fu says it is stored unencrypted for some malware, that might be on my computer, to read.

---

### Post by kevdog on 2021-01-14
I like KeyPassXC a lot.  I've also setup a self-hosted BitwardenRS server that I self host.  It's a lot more robust at sharing passwords across devices and syncing.  I access the server via a VPN and it tends to work pretty well.   I'm surprised this didn't make the list.

---

### Post by llamabr on 2021-02-02
> **kevdog said:**
> I'm surprised this didn't make the list.

Hi, Kevdog. It didn't make the list because I don't know anything about it -- I tried to include a number of choices, but it's not comprehensive or exhaustive at all. It's also basically a commercial for "pass", which I just switched to. I also link to a post I made a few years ago which includes a number of other applications, including KeePassX.

Your system does sound very attractive, though. Could you give some more details about how one might go about setting it up?

---

### Post by TheFu on 2021-02-02
Web-based password managers scare me. There are so many ways that web-apps can be compromised, it just scares me.  I don't have any specific knowledge about a hack against any web-app-password managers, but there are so many hacking tools, so many experts at hacking those things, and they are a very rich target for seeking out methods w/ techniques.  

Sorta like why I don't like web-based system admin, DBMS, and LDAP management tools. There are just too many risks to mitigate those things from being hacked.

---

### Post by lordgallen on 2021-03-08
One way to possibly thwart an attack on a web based password manager is to salt your passwords.

---

### Post by kevdog on 2021-03-11
Hey sorry about the late review.  

I had Ubuntu or some linux variant installed on a few laptops for years and I can't say other than using the machines I did anything great with my linux installations.

The last year and a half however (maybe two), I've embarked on a few interesting projects which for me have definitely stretched my linux/computer/networking knowledge. I'm not an IT guy and have no formal training so for me it was a pretty good adventure. I've learned about the power of virtualization, zfs (snapshots and backups), and running things via containers.  

My setup is consists of a couple of different components (however these components could be combined if you didn't have a larger budget).
1. Virtualized pfSense router - [https://pcpartpicker.com/b/7ctgXL](https://pcpartpicker.com/b/7ctgXL)
1a. Xcp-NG hypervisor - [https://xcp-ng.org/](https://xcp-ng.org/)
1b. Virtualized Ubuntu Install (Located on same physical hardware as pfSense) which runs Xen-Orchestra (Graphical frontend to xcp-ng hypervisor).  
2. FreeNAS virtualized Ubuntu installation - [https://www.truenas.com/](https://www.truenas.com/)
3. Bitwarden_rs docker installation within Ubuntu install with postgresql backend for DB storage - [https://github.com/dani-garcia/bitwarden_rs](https://github.com/dani-garcia/bitwarden_rs)
4. Virtualized Linux install running reverse proxy (prior Linux install was Ubuntu, now Arch) and Reverse Proxy (flipping and flopping back between nginx, nginx proxy manager, and traefik).  

TheFu is big on KVM virtualization which I can't argue with.  I've never really used KVM straight up an a plain Ubuntu installation.  Not being an IT guy I started with ProxMox which is a debian based Type I hypervisor.  I liked the product a lot but I don't think I was very adept at finding information out about how to do things.  I didn't find the ProxMox forums to be that useful of a resource nor was Reddit.  I'm sure I'd be much better with ProxMox now, how that's after a couple of years after working with a hypervisor.  I chose xcp-ng as hypervisor which is an open source citrix based type I linux hypervisor running on top of CentOS.  I found videos on how to setup xcp-ng via Tom Lawrences's channel - [https://www.youtube.com/channel/UCHkYOD-3fZbuGhwsADBd9ZQ](https://www.youtube.com/channel/UCHkYOD-3fZbuGhwsADBd9ZQ).  These videos do excellent job at walking a beginner through the steps on how to set up xcp-ng from scratch on new machine. Gui management tools for xcp-ng include either Xen Orchestra ([https://xen-orchestra.com/#!/xo-home](https://xen-orchestra.com/#!/xo-home)) or Xen Center ([https://github.com/xcp-ng/xenadmin/releases](https://github.com/xcp-ng/xenadmin/releases)).  Xen Center is a windows only client where Xen Orchestra is a web based application which needs to be run within linux host.  The good news about the Linux Host is that the host can be virtualized within xcp-ng so both the hypervisor and GUI frontend can be run on same machine (Actually one Xen Orchestra installation is capable of managing many many xcp-ng hypervisors so it would be possible to cluster a bunch of hypervisors controlled via one XO installation).  XO can be installed within linux from source -- or I use the Jarli scripts ([https://github.com/Jarli01/xenorchestra_installer](https://github.com/Jarli01/xenorchestra_installer) and [https://github.com/Jarli01/xenorchestra_updater](https://github.com/Jarli01/xenorchestra_updater)).  Really easy to get a hypervisor up and running knowing basics with functional GUI after watching a few videos and doing some reading

Although not essential I wanted to upgrade my home router of the usual Linksys stuff, and I actually didn't find DD-WRT to be all that useful either.  pfSense allows me to have an enterprise router for free (well I have to provide the hardware), that offers capabilities for network firewalls, VLANs and GeoIP/site blocking, and DNS Resolution -- via there DNS Resolver known as Unbound.  It will also perform all DNS requests over DOT if you would like.  It also offers VPN capabilities via OpenVPN or WireGuard (wireguard newest implementation just released on newest release 2.4.5 which I haven't tried).  I've setup OpenVPN client and servers before on Ubuntu installations, however the OpenVPN implementation on pfSense is really easy. Tom Lawrence once again has a bunch of videos on setting up OpenVPN (which are older) or Wireguard (which is newer) which really makes the process very straightforward.  Although I haven't really had a lot of time to play with the wireguard stuff, the OpenVPN stuff is pretty dang easy.  There are OpenVPN clients which I personally use Viscosity on Mac and OpenVPN app (on iPhone/Android). OPNSense ([https://opnsense.org/](https://opnsense.org/)) is a fork of pfSense which also offers these capabilities. I'm aware many users on this forum use OPNSense as their router software -- I'm just not familiar with this fork. 

Another big piece of the equation for me was running a reverse proxy.  I was familiar with Apache, however I became more familiar with Nginx particularly after self hosting a Nextcloud installation which I used nginx as a webserver and reverse proxy.  I did everything by hand initially in terms of writing the config files and read a lot of the documentation and looked at a lot of examples.  I guess this was a good learning experience although I cant say the process was easy as I made a lot of mistakes. I learned how to incorporated Let's Encrypt SSL Certificates, purchased a domain name, and am using Cloudflare as my DNS registrar and host.  Other than the domain name, all the rest of the steps and services are free.  Mozilla SSL configurator [https://ssl-config.mozilla.org/](https://ssl-config.mozilla.org/) is a really good resource to use helping to setup the reverse proxy.  I originally used the utility certbot which is written by the Let's Encrypt people for auto renewal of the certificates, however I'm now running either Acme.sh via a systemd timer/service or using a proxy such as Traefik which will do the LE SSL cert management automatically.  Caddy is another option as a reverse proxy that will do automatic SSL certificate management.  I've never played with this reverse proxy so I can't speak a lot about it.  Supposedly its super easy.  Nginx Proxy Manager is yet another option to do automatic SSL certificate management however NPM (Nginx Proxy Manager) is a docker container -- and at the time I knew jack crap about running docker containers so this really wasn't an option for me initially.  I'm running Syncthing on my LAN with an NPM reverse proxy -- it's pretty easy, however I admit it doesn't generate the cleanest config files and there were a couple of instances (well more than a couple) I added configuration based on the stuff I learned by writing the config files by hand. It's good at the certificate management, but I admit it could be a heck of a lot better at helping generate cleaner configuration files with options. pfSense also has a built in reverse proxy known as HA proxy.  I tried HA Proxy out however the version within pfSense is really old and some of the newer features I needed -- so I just decided to forego HA proxy, and forward 80/443 to an internal VM running my reverse proxy.  


My actual Bitwarden Linux VM host is virtualized with FreeNas (now known as TrueNAS).  FreeNAS is yet another wonderful project which will really open up a lot of knowledge. It runs on FreeBSD which you don't have to know a lot about BSD to use however occassionally I have to look things up.  FreeNAS has a built in hypervisor known as bhyve.  People complain about bhyve as a hypervisor - comparing it to Proxmox or ESXI -- however for running a straight non graphical linux server -- its super easy.  One thing I do like about FreeNAS is the ability through zfs to take snapshots of the VM. Snapshots are great since if you totally screw something up, you just revert to the snapshot. Snapshots are delta based so they don't take up a bunch of storage if you frequently snapshot and its pretty easy to restore.  I'm aware since OpenZFS can be used in linux, that Proxmox now can use ZFS (at the time it was available really to BSD variants).  People still complain that the ZFS stuff is "out of tree" meaning the modules need to be added in and aren't part of the linux kernel.  If you've ever done any kernel updating via DKMS, you'll see how the ZFS modules need to be added via mkinitcpio to produce the ramdisk. Some people don't like this implementation, however I really like ZFS and think its great for a server. FreeNAS has taught me a lot about ZFS

In terms of docker -- damn --- it's just straight easy.  Learn docker in conjunction with docker-compose, look at the example docker-compose files provided with the project, and just start.  Of all the things I've needed to learn, docker was probably the easiest.  If you need my docker-compose setup for bitwarden_rs, I'll provide one, since its really easy.  I've started using a database as a back end (such as postgresql although I do have a test install with mariadb) only because there are utilities (such as other docker containers), you can set up to back up and dump the database remotely. It's just another means to protect against data loss in addition to snapshotting (which is kind of a crude back up strategy). 

Anyway I think bitwarden_rs is a great project to start out if you really want to explore some concepts about virtualization, networking, docker and docker networking, SSL certs, reverse proxies, etc.  Combine with a VPN for remote access (if you need this since BW is really good about caching things on the client), and I think its a really secure solution

I also run KeePassXC and its pretty good for like one client, however if you need passwords to be accessible across a wide range of devices, then I think a server solution is more versatile.  

Sorry about the rant.

---

### Post by TheFu on 2021-03-11
> **kevdog said:**
>  
I also run KeePassXC and its pretty good for like one client, however if you need passwords to be accessible across a wide range of devices, then I think a server solution is more versatile.  

Sorry about the rant.

Good stuff in that post!  Always good to read how smart people do things just a little different.

The power in KeePass variants is in the shared database.  That means any software that can use the same KeePass DB, can be used, on any platform.
I have automatic cloning of my kdbx files nightly. They get pushed from 1 system (I call it the "system of record") out to about 6 other locations. That's in addition to normal backups performed on all those systems.  I don't use the KeePass program on Linux mainly because it requires Mono and I find that bloated.  I use KeePassXC on Linux.  I use a different KeePass-compatible app on Android and something else on that OS that cannot be named.  

I keep all sorts of data inside my KeePass.kdbx file(s).  Because I know it will not be lost over dumb things, important data gets stored inside it - like banking, insurance, house, car, credit cards, software license keys, passports, immunizations, and travel plans.  I once traveled to Asia for 3 weeks and left my portable tablet with all my trip data on it in the car back at the airport parking at home. I didn't even know the name of the hotel were I planned to stay the first week.  But I did have a thumb drive with portable apps and my KeePass DB.  I found a hotel that let me use their guest PCs for a few minutes to look up the data, then used google-maps to find it and get there.
[https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager) has more ideas for stuff to put into your password DB.

I've got to say 1 more thing.  IMHO, a WAN router needs to be a separate, physical device. It should never be virtualized, except in an emergency, for a few hours.  There are just so many things that can go wrong with virtualization and a properly configured WAN gateway/router is just too scary to me to risk it.  I love virtualization, but not for that purpose.  I use OPNSense, but have used pfSense for years before and dd-wrt, tomato, and a few other router distros.  
On my LAN, I do use OPNsense as a LAN router and run that inside a VM. That's a completely different risk level.  It has a dedicated NIC just for the router VM to connect to other subnets.

---

### Post by lordgallen on 2021-03-11
I have been using bitwarden going on two years now, and I don't believe that I have experienced any breaches, however, what would be an attack vector for bitwarden? I use the extension for Brave and Firefox Browsers, and I also have the app installed on my android phone. From what I understand the data is encrypted on bitwarden's servers, so if they were hacked, the data would be worthless to hackers correct? On Ubuntu I have the firewall turned on to the basic settings, and I always log out of the extension after each login. On my Samsung phone, I have it protected on the hidden folder, by Samsung Knox.

---

### Post by T6&amp;sfpER35% on 2021-03-11
every time i read about password managers i feel like i have to share this tip , i think it's brilliant.
its the double blind password ,basically you don't know the password in the password manager (cause it's such a random long one) ,and the password manager doesn't know the full password either cause you add another password at the end of the saved password in the password manager. So you have to remember two passwords, the master password and your "adding" password.
anyway , [this](https://www.allthingssecured.com/tips/password-security/double-blind-password-strategy/) will explain it better .

---

### Post by kevdog on 2021-03-12
> I've got to say 1 more thing. IMHO, a WAN router needs to be a separate, physical device. It should never be virtualized, except in an emergency, for a few hours. There are just so many things that can go wrong with virtualization and a properly configured WAN gateway/router is just too scary to me to risk it. I love virtualization, but not for that purpose.

I don't have any background in IT at all and I've heard this statement made from other sources as well.  I've a virtualized pfSense WAN router for almost two years.  Took me a while to setup particularly with all the VLAN tags but I haven't had any problems with the setup.  Should I be expecting any problems?   I'm just curious.  The only thing that makes me nervous with the entire setup is hypervisor upgrades -- which I've luckily survived two without incident.  Maybe I'm just lucky or just cheap given it's for home use.

[https://imgur.com/dPw58m0]("https://imgur.com/dPw58m0")
91 day uptime -- loving that!!

---

### Post by DuckHook on 2021-03-13
> **kevdog said:**
> …I've a virtualized pfSense WAN router for almost two years.  Took me a while to setup particularly with all the VLAN tags but I haven't had any problems with the setup.  Should I be expecting any problems?   I'm just curious.  The only thing that makes me nervous with the entire setup is hypervisor upgrades -- which I've luckily survived two without incident.
Like you, I have no technical background. But speaking purely personally, like TheFu, I would be very concerned with such a setup. All containers including VMs have both known and unknown holes. I wouldn't want to give the scumbags another attack surface. That alone would deter me from ever doing what you've done.

Now, I get that a standalone machine also has known and unknown holes. But as a standalone, I would not be doubling up my exposure. Moreover, I suspect (though I have no way of proving this) that finding holes in a virtual environment is a lot easier than a physical one. If so, then the risk instantly more than doubles. Not least, the added layers/protocols constitute another attack surface. How confident can we be that VLAN tagging itself is secure?

I suppose that we must each reach our own conclusions about what level of exposure we are comfortable with. I run my Kodi boxes on the same network as my fileservers. I know TheFu would never do that. I will say that I am thinking of completely segregating them, but it's a project of dismaying complexity.

---

### Post by kevdog on 2021-03-13
> **DuckHook said:**
> 
I suppose that we must each reach our own conclusions about what level of exposure we are comfortable with. I run my Kodi boxes on the same network as my fileservers. I know TheFu would never do that. I will say that I am thinking of completely segregating them, but it's a project of dismaying complexity.

Well @DuckHook have you ever thought of using VLANs for network isolation for you Kodi boxes?  You'd have to have a capable router and if there is a switch in the mix it would need to be a managed switch.  Just thought I would ask. VLAN isolation is NOT complex. Stick a firewall in front of the Kodi boxes to limit exposure and that should definitely help.

---

### Post by DuckHook on 2021-03-13
> **kevdog said:**
> Well @DuckHook have you ever thought of using VLANs for network isolation for you Kodi boxes?  You'd have to have a capable router and if there is a switch in the mix it would need to be a managed switch.  Just thought I would ask. VLAN isolation is NOT complex. Stick a firewall in front of the Kodi boxes to limit exposure and that should definitely help.
VLANs were the first thing that came to me. BTW, it was you and TheFu who planted the seeds of this idea in my head in response to my Nextcloud thread (I believe), so I have you to thank for this brainworm that now won't go away. :-({|=

The servers are the problem. My data is all mashed together. So I would have to extricate the various files and segregate them onto separate servers, whether physical or virtual. It's more of a chore than a real roadblock, but it's dismaying all the same.

My conundrum arises because this problem is only a recent one. The Mrs and I have only recently introduced KODI to our lives. Prior to that it was POTS telephony and cable. The Internet was isolated from everything else. I was dealing with a simple NAT LAN and one egress point to the WAN. Easy as pie. This pandemic and its enforced isolation inspired me to make wholesale changes to my LAN including VoIP, OTA Antennae+TV tuner, KODI, cord cutting, business grade IP and Nextcloud, all harbouring unintended consequences that I am only now wrestling with.

It makes my old brain hurt. ](*,)

---

### Post by kevdog on 2021-03-13
> **DuckHook said:**
> 

The servers are the problem. My data is all mashed together. So I would have to extricate the various files and segregate them onto separate servers, whether physical or virtual. It's more of a chore than a real roadblock, but it's dismaying all the same.


I hear you on this problem.  I run into this problem many times for a home lab where you spin something up as a "test" case and months or years later your "test case server" has taken on a life of it's own -- storing data and other files now your dependent upon in manners you didn't plan for".  I'm now of the mindset that each server such as nextcloud, kodi, bitwarden, etc get's it's own VM with an appropriate backup plan that somehow copies/mirrors/synchronizes the data to a different physical machine if possible. I'm aware of the 3-2-1 rules of backup, however I don't have an offsite at the moment.  

Sometimes when tying to segregate out the data I just kind of start over reproducing the server and extracting what I think need -- it's kind of like spring cleaning if you know what I mean.  In starting over I try to incorporate some of the other concepts of network isolation, file sharing and backups into the new design.  I've been willing to incorporate docker containers which takes away some of the maintenance tasks of some of these servers which I'm sure some would frown upon.  I'm sure I'll reach a point in the future where I'll look back on my second go around of server recreation and shake my head saying -- I should have done it this way or that, which is part of the problem with my lack of experience.  

Dont make your head hurt -- it's all kind of fun in the end right??

---

### Post by DuckHook on 2021-03-13
> **3nd said:**
> every time i read about password managers i feel like i have to share this tip , i think it's brilliant.
its the double blind password ,basically you don't know the password in the password manager (cause it's such a random long one) ,and the password manager doesn't know the full password either cause you add another password at the end of the saved password in the password manager. So you have to remember two passwords, the master password and your "adding" password.
anyway , [this](https://www.allthingssecured.com/tips/password-security/double-blind-password-strategy/) will explain it better .
This is a way&#8209;cool technique. Thanks for posting.

---

### Post by DuckHook on 2021-03-13
> **kevdog said:**
> …when tying to segregate out the data I just kind of start over reproducing the server and extracting what I think need -- it's kind of like spring cleaning if you know what I mean.
Exactly what I intend on doing.
> In starting over I try to incorporate some of the other concepts of network isolation, file sharing and backups into the new design.
Again, my plans echo yours.
> I've been willing to incorporate docker containers which takes away some of the maintenance tasks of some of these servers which I'm sure some would frown upon.
In my case, LXD, but same principle.
> it's all kind of fun in the end right??
Of course. It all takes time and it's often two steps forward, one step back, but the learning keeps my mind active and I do find the whole field both challenging and fascinating.

Thanks for the tips!

---

