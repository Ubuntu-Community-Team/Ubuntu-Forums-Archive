---
title: "UbuntuOne working on Kubuntu"
date: 2010-07-01
forum: Ubuntu One (CLOSED)
---

### Post by NUboon2Age on 2010-07-01
The following draws upon [Joshua Hoover's answer]("https://answers.edge.launchpad.net/ubuntuone-client/+faq/594")

7/17/2010

[SIZE="2"]**Verified with a clean install of Kubuntu (64 bit) and an [ Updated summary of Harald Sitter's instructions]("http://ubuntuforums.org/showpost.php?p=9548989&postcount=4")**[/SIZE] (post 4)

[SIZE="4"]**ubuntuone-kde File Syncing Working!!!  Here's how:**[/SIZE][SIZE="2"]
[LIST=1]
[*] Add Harald's ppa to Kubuntu's repositories:
    deb [http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu](http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu) lucid main 
    deb-src [http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu](http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu) lucid main 
[*] Install ubuntuone-kde.  The packages ubuntuone-api0, ubuntuone-client, and python-ubuntuone-client should have been installed also.
[*] *Note: [7/9/2010: Harald has now updated the packages]("https://answers.edge.launchpad.net/ubuntuone-client-kde/+question/116847") so the patch he talks about in his instructions are no longer necessary.
[*] Applications->System Settings->Network and Connectivity->Ubuntu One settings (ie. the KCM)->Manage Account. That takes you to the Ubuntu One web site and prompts you to add the machine to the account. Add it.
[*] Start the Applications->Utilities->Status Notifier for Ubuntu One, Tell it to connect to Ubuntu One.  
[*] Verify the files from Ubuntu One show up on the Kubuntu (in my case a Wubi install Kubuntu) computer.  Both the /home/Ubuntu One folder and the UDFs I'd created previously on my Ubuntu machine. Yeah!!!  
[*] Note: I didn't try Dolphin integration yet (which I assume would allow me to create new UDFs from my Kubuntu machine).[/SIZE]
[*] I confirmed Tomboy Notes synchronization is working.
[/LIST]

---

### Post by NUboon2Age on 2010-07-05
To **install the UbuntuOne service on Kubuntu w/ ubuntu-gnome-client** for the UbuntuOne client 

 I found:   [http://www.ubuntugeek.com/how-to-install-ubuntu-one-on-kubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-ubuntu-one-on-kubuntu-9-10-karmic.html)  which said:

**[SIZE="3"][LIST=1]Install client**[/SIZE]> "You need ubuntu-one-client-gnome to install and work.
    Use the following command to work"
  ```
**sudo apt-get install ubuntuone-client-gnome**
```
      -OR-
    Click on the following link to install
  **[apt://ubuntuone-client-gnome]("apt://ubuntuone-client-gnome")**


**[SIZE="3"][*]Add this computer to syncing[/SIZE]**
Then the #ubuntuone irc channel provided:
   [http://bit.ly/caHbOf](http://bit.ly/caHbOf) 
     from which i used this:
       ```
** u1sdtool -q; killall ubuntuone-login; u1sdtool -c**
```
        A message that sync daemon had been stopped came up which told me that something was working.
        Then it took me to a web page to add my computer.  All seemed to work until after the last step when 
             i got an "Ubuntu One Error" (with no further details provided).
[/list]
**[SIZE="2"]Confirm[/SIZE]**
        1) Despite the vague error message I checked on my desktop and see all my synced files and folders are there so it seems to be working.
         2) I did a ```
**ulsdtool -s**
``` (check sync daemon status) and it says its running.

[SIZE="3"]**Apparent success.**[/SIZE]

---

### Post by NUboon2Age on 2010-07-05
[SIZE="4"]**Notes on the experiment:**[/SIZE]

**NOTE/CAVEAT**: I had **previously set up UbuntuOne using an Ubuntu machine**, so I'm not 100% sure in what ways this affected my result and how it would have been if I hadn't done that first.  Also I've entirely concentrated on **the most basic file syncing and Tomboy notes** and haven't experimented with addressbook sync or music from U1

**NOTE:** I saw some other web pages about work on **getting ubuntuone-kde working**, i tried several.  [This one]("http://maketecheasier.com/how-to-install-and-setup-ubuntu-one-in-kubuntu/2010/03/15") was basically a non-starter -- seems like the package and program names have changed. 

**NOTE:** For now I haven't discovered how to start any graphical client front end to check and see if it were working. 

About this over on the #ubuntuone irc channel  Chipaca reported 
> "as it stands, the file sync aspect of Ubuntu One gives very little feedback about what's going on, which you might find disconcerting until you get a feel for how it works...
you can install magicicada to help you understand what's going on
```

sudo add-apt-repository ppa:chicharreros/ppa; 
sudo apt-get update; 
sudo apt-get install magicicada

```

Notes: 7/2/2010
[SIZE="3"]**File syncing appears to be working using my install of ubuntuone-kde**[/SIZE] I still haven't found a GUI feedback mechanism for the UbuntuOne stuff in KDE.  I haven't experimented yet with John Lenton's Magicidada, so that might help...

Notes: 7/4/2010
**The UDFs problem: **
UDFs = User Defined Folders: any folders you've designated to be synced in Ubuntu One other than the default "Ubuntu One" folder and its default "Shared With Me" Folder within.
 
If you run into a situation where other synced folders (that you designate as Ubuntu One synced folders besides the "Ubuntu One" folder which are are not propagating to your desktop it could be because UDFs are not supported on your system.  I didn't observe whether the is the case on my Kubuntu Lucid when I was using ubuntu-gnome-client as I describe above or not.  With ubuntuone-kde (installation described in post #3) I was getting UDFs previously created in Ubuntu and synced to U1 to propagate to my Kubuntu desktop, but I wasn't able to designate new UDFs from within Kubuntu.  I believe this is the 'Dolphin Integration' that Harald Sitter refers to below in post #4. 

Here's what Canonical's U1 developer of ubuntu-client-gnome, John Lenton (Chipaca on #ubuntuone irc channel) explained about UDF support:> 
<Chipaca> Karmic didn't have UDFs :) 
so, you could use a backport of ubuntuone (from the ubuntuone-hackers ppa) 
on Karmic, and get the UDFs or just not use UDFs at all -- your choice.

**Questions I asked Harald Sitter:**

1) Q: (Clarification on installation instructions ubuntuone-kde).

A: Harald says if you install ubuntuone-kde it should automatically install ubuntuone-api0, ubuntuone-client, and python-ubuntuone-client. 

Or as Harald's put it: From [https://answers.launchpad.net/ubuntuone-client-kde/+question/116847](https://answers.launchpad.net/ubuntuone-client-kde/+question/116847)
> "ubuntuone-kde -> patch -> run
ubuntuone-kde ought to depend on libuntuone-api0 which depends on ubuntuone-client which depends on python-ubuntuone-client, which contains the file that needs patching."

2) Q: In your instructions you refer to 'KCM'.  What is a KCM?  
A: KCM is an acronym for KDE Configuration Module, each "applet" that you find in "System Settings" is a KCM.

Harald, Thanks ahead of time for your hard work on this project and for taking the time to respond to questions.

---

### Post by NUboon2Age on 2010-07-05
[SIZE="3"]**Here's a note from Harald Sitter re: ubuntuone-kde**[/SIZE]
[https://lists.ubuntu.com/archives/kubuntu-devel/2010-June/004436.html](https://lists.ubuntu.com/archives/kubuntu-devel/2010-June/004436.html)
> Ubuntu One KDE UI sort-of alpha1
Harald Sitter apachelogger at ubuntu.com
Sun Jun 13 14:20:02 BST 2010

I am currently working on my Google Summer of Code project where I am to bring 
better Ubuntu One experience to KDE users. This project is divided into two 
parts, one being user interface integration and the other is data integration 
(a.k.a. Akoandi support).

In ppa:apachelogger/ubuntuone-kde you can now get a pretty much working Alpha 
1 of the user interface integration, only that it is not really Alpha 1.

BEFORE installing please read everything below and be warned that this is all 
work in progress and I will most likely not provide seamless upgrade 
experience, so it would be best if you know how to resolve file conflicts in 
DPKG and the like.

So first let me state why it is not the real alpha...
Unfortunately the Ubuntu One SyncDaemon (the component that is responsible for 
interacting with the Ubuntu One cloud) does in its current stable iteration 
only support the GNOME keyring as secret storage unit. But for sensible 
integration into KDE the authentication and therefore the secret storage must 
be handled by KDE components, most importantly KWallet. [b](*Ignore the next  
sentence -- it no longer applies since Harald Sitter corrected this.)[/b]  [I]So in order 
to make everything work properly you need to patch the SyncDaemon. [1] provides 
a one-line command to do this, which basically just applies a patch [2] to your 
SyncDaemon exchanging the gnome-keyring support for KWallet support.[/I]

Once you have that done you should install ubuntuone-kde and relogin, after 
that you can safely try using the KDE integration. It should be noted that 
using the KCM first will not work, and I am not sure about Dolphin integration 
(testing please?).

You can use the Dolphin integration only if you place a .ubuntuone file in the 
directory you want to use it with (also with 4.5 beta2 you will need to turn 
on the plugin via the Dolphin settings, it will show up there as a version 
control plugin).

The statusnotifier item (fancy systemtray icon) can be started via ubuntuone-
statusnotifier, or via the utilities section of your menu.

A configuration module is to be found in your systemsettings, currently it 
will just display information queried on-the-fly from the Ubuntu One servers.

Authentication is handled by ubuntone-auth.

What I ask you to do is give it a good test run and start crying really bad 
should you encounter:
a) a crash
b) nothing
c) clearly wrong behavior
d) stuff that you think I did not think of, but seems worth mentioning

Tech Talk:
StatusNotifier and Dolphin integration use libubuntuone-kde which basically 
provides an interface to the Ubuntu One SyncDaemon, upon status changes this 
beastie should emit the appropraite information so that the StatusNotifier can 
react properly. Another implementation of using the SyncDaemon is available in 
the source [3] as a proof of concept plasmoid.
The KCM uses libubuntuone-qt-api which is a Qt interface to the Ubuntu One 
server side REST API (hence this thing is mosty asynchronious). Please note 
that the KCM will not work unless you used the statusnotifer before, because 
it will be missing authentication information and at this time does not 
trigger the auth process itself. If you wish you can also try creating own 
apps to test the API implementation, currently the KCM does not use the API to 
its full extent, though it probably will do once I am finished.
Ubuntuone-auth registers to DBus and provides the same interfaces as the GNOME 
version provides, so technically one could also use it with the GNOME UI ;) 
(that is if someone really wants to hook it up with gnome-keyring). One 
technical point of interest is that it will launch an own tiny HTTP server for 
the authentication process, this will then lead to a fist-start workflow like:
1) you start an U1 app 2) webbrowser opens asking you if you want to auth the 
machine you are on to use U1 3) you either agree or decline 4) U1 server calls 
back to local HTTP server and transmits some tokens through the URL 5) 
ubuntone-auth requests access tokens and tells the app(s) about arrived 
credentials.

[1] [http://people.ubuntu.com/~apachelogger/ubuntuone/HOWTO](http://people.ubuntu.com/~apachelogger/ubuntuone/HOWTO)
[2] [http://people.ubuntu.com/~apachelogger/ubuntuone/syncd-kwallet.patch](http://people.ubuntu.com/~apachelogger/ubuntuone/syncd-kwallet.patch)
[3] [https://code.launchpad.net/~apachelogger/ubuntuone-client/gsoc](https://code.launchpad.net/~apachelogger/ubuntuone-client/gsoc)

----------------------
While I am at it, let me also give a quick heads up on the Akonadi stuff.

At [4] and [5] you can find components started by Till Adam some time ago 
laying out very good basics for addressbook integration with Akonadi. If you 
are very, and I mean VERY, brave, then you might try it out. Although 
currently it will only (almost completely) map Ubuntu One contacts into 
KAddressbook processable ones. Everything else will result in undefined 
behaviour. Also please note that authentication to desktopcouch is not 
implemented, so you will need to turn off authentication in your desktopcouch 
config.

[4] [https://code.launchpad.net/~apachelogger/+junk/couchdb-qt](https://code.launchpad.net/~apachelogger/+junk/couchdb-qt)
[5] [https://code.launchpad.net/~apachelogger/+junk/akonadi-desktopcouch](https://code.launchpad.net/~apachelogger/+junk/akonadi-desktopcouch)

-- 
Harald Sitter
Kubuntu Core Developer
[http://www.kubuntu.org](http://www.kubuntu.org)


---

### Post by NUboon2Age on 2010-08-06
From [https://lists.ubuntu.com/archives/kubuntu-devel/2010-July/004489.html](https://lists.ubuntu.com/archives/kubuntu-devel/2010-July/004489.html)

> Harald Sitter apachelogger at ubuntu.com
Sun Jul 11 13:40:39 BST 2010



Just a quick heads up. As of recently the PPA provides its own sync daemon  package that is able to handle both kwallet and gnome-keyring. Therefore patching is no longer necessary.

If you have time please give this a good amount of testing (also using the gnome client). The changes I applied ontop of syncdaemon are now trying to be non-intrusive to the gnome-keyring side of things and I am planning on pushing it into the official packages soonish.


Technical rambling---
[http://bazaar.launchpad.net/~apachelogger/ubuntuone-client/stable-1-2-](http://bazaar.launchpad.net/~apachelogger/ubuntuone-client/stable-1-2-)
lucid+kwallet/annotate/head:/debian/patches/01syncd-kwallet.patch

kcheckrunning is used to check whether we are running in a KDE session. We cannot use KDE_FULL_SESSION because dbus service invoked apps do not have a proper environment (syncd being started by dbus is affected by this). kcheckrunning however should be more reliable (at least it is used in startkde 
:)).

If KDE is running we will try to get the tokens from kwallet, if that fails we try to use gnomekeyring (covering the case where KDE is running but not ubuntuone-kde is used). If no KDE is running everything behaves as previously.

There is a particular concern that sometimes for me syncd got stuck, upon killing it spit out a backtrace to the assignment of "wallet". By painful trial and error I concluded that the problem is that the QCoreApplication is not destroyed once the function gets left, making kwallet fall over at a subsequent call to that function since it requires a QApp to use its QEventLoop but now got 2 QApps :/. That is supposedly fixed by first trying to get an existing instance (via the static interface QCoreApplication::instance()) and if that yields None we create an instance. 

Yet I am not entirely convinced that solved it properly. Also this is sort of ugly. So I was thinking about a helper cpp app that would try to get the token, which would get called by syncd. From looking at the code you will notice that it really is a major uglyness as it is.

-- 
Harald Sitter
Kubuntu Core Developer
[http://www.kubuntu.org](http://www.kubuntu.org)

---

### Post by neanderslob on 2010-09-07
Hi all,

I'm having the weirdest difficulty installing the package ubuntuone-kde.  Essentially, after adding the prescribed repository and updating, it still doesn't come up with that package.  See below.

```
sam@megaladon:~$ sudo add-apt-repository ppa:apachelogger/ubuntuone-kde
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv AEFEA337B2F7FE9222289A46ADAA0E064427DF3B
gpg: requesting key 4427DF3B from hkp server keyserver.ubuntu.com
gpg: key 4427DF3B: "Launchpad PPA for Harald Sitter" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
sam@megaladon:~$ sudo apt-get update && sudo apt-get install ubuntuone-kde 
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Hit http://ppa.launchpad.net lucid Release                                     
Get:1 http://packages.medibuntu.org lucid Release.gpg [197B]                   
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Get:2 http://packages.medibuntu.org lucid Release [6,854B]                     
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid-backports Release             
Hit http://packages.medibuntu.org lucid/free Packages                          
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources      
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-backports/main Packages
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources
Fetched 7,051B in 1s (5,193B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntuone-kde
```

I've tried adding the repository manually as well with the same result.  The strangest thing is that I KNOW this works because I did exactly this to get it working on my computer a few weeks ago (before I reinstalled my OS because I did something unrelated and dumb).  Am I missing something obvious here?  I feel like I must be. ](*,)

---

### Post by NUboon2Age on 2010-09-10
[https://bugs.launchpad.net/ubuntuone-client/+bug/375145](https://bugs.launchpad.net/ubuntuone-client/+bug/375145)

Harald Sitter wrote:

> Actually the major part ... is already done since I abandoned social life to come up with a UI for ubuntu-sso-client
[https://code.edge.launchpad.net/~apachelogger/ubuntu-sso-client/kdeui](https://code.edge.launchpad.net/~apachelogger/ubuntu-sso-client/kdeui)

What is missing is kwallet support and fitting the pieces together once
more.

---

### Post by NUboon2Age on 2010-09-10
> **neanderslob said:**
> Hi all,

I'm having the weirdest difficulty installing the package ubuntuone-kde.  Essentially, after adding the prescribed repository and updating, it still doesn't come up with that package.  See below.

...

I've tried adding the repository manually as well with the same result.  The strangest thing is that I KNOW this works because I did exactly this to get it working on my computer a few weeks ago (before I reinstalled my OS because I did something unrelated and dumb).  Am I missing something obvious here?  I feel like I must be. ](*,)

Why not either add to [bug #375145]("https://bugs.launchpad.net/ubuntuone-client/+bug/375145") or write a new one?  We need to get this working on Kubuntu/kde.  Unfortunately i don't have my Kubuntu install up right now to experiment with.

---

### Post by NUboon2Age on 2010-10-26
I created a Launchpad team [SIZE="4"]for all of us interested in getting Kubuntu working on Ubuntu One[/SIZE].  Its called [SIZE="5"]**[KUbuntuOne]("https://launchpad.net/~kubuntuone")**[/SIZE].    Membership is open (at least for now or until the group decides it needs to be moderated), so please [SIZE="5"]**come join us**[/SIZE].:guitar:\\:D/

---

### Post by ronnoc on 2011-04-09
I joined! Hope to see some movement out of this soon. If I can be of help, let me know. Thanks.

---

### Post by neanderslob on 2011-04-15
That's pretty cool; does it interface with UbuntuOne?  See, I've been known to use both KDE and Gnome on different computers which was really my reason for asking in the first place.  I've since just used dropbox, to which I've become rather attached but I'm curious.

---

