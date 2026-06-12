---
title: "GuiSamba Spec discussion"
date: 2006-04-30
forum: Server Platforms
---

### Post by troyDoogle7 on 2006-04-30
I have started a fresh post just to keep things tidy. so that the devs of [http://wiki.ubuntu.com/GUISambaConfigSpec](http://wiki.ubuntu.com/GUISambaConfigSpec) can read some constructive feedback and perhaps help formalise the design.

This is a continuation from [http://ubuntuforums.org/showthread.php?t=25887&page=3](http://ubuntuforums.org/showthread.php?t=25887&page=3)

---

### Post by troyDoogle7 on 2006-04-30
mci8406 gave some great feedback
> 
That sounds good troy. I found some specs on the wiki: [http://wiki.ubuntu.com/GUISambaConfigSpec](http://wiki.ubuntu.com/GUISambaConfigSpec)

Here are some of the thoughts I had:

    * Python + GTK for the interface
    * Configure server/workstation Options
          o hostname
          o workgroup
          o description
          o advanced options
                + master browser status
                + other (theres quite a few advanced options that arent needed by everyone, but perhaps we should include the most common ones here)
          o (share) Security mode (maybe advanced option?)
    * Shares config
          o path to share
          o share name
          o share description
          o share security (opens as seperate dialog?)
          o mount/exported shares
    * user account management

Perfect! Couldn't have said it better myself

> 
I think that covers the features that most people need in a simple setup.
Nautilus seems to have decent samba client support (at least in dapper). The browse list is empty for me, but if I type in the machine's name directly, it is accessible. I haven't determined if that is a problem with the browsing interface in nautilus or with my system's config. If anyone can tell me if it works, that would be great.

The idea of giving the user the option to select which version of windows (described in the wiki) they want samba to emulate is an interesting idea. I dont think options described above should be replaced with it, but maybe allow for both? Also, by giving that option some people may not necessarily pick the best option for their server; they may instead pick win95 emulation because they are used to that version or think they have to pick that to make it work with win95 clients. Perhaps a better option might be to describe the user/share/domain options in detail, and give examples (i.e. share is like win95).
I think its a valid point that us noobs would pick something that we recognise.  I think most noobies won't know what system each windows networking environment uses.  I firmly believe we should emulate the windows xp network wizard style.  Its simple and to the point.  We can add some extra options for samba users etc, but we want to keep it simple otherwise we will a) have a support problem b) be back to square 1 in terms of complications.

> I'm not currently familar with the "usershare" support the wiki says is going to be in the new version of samba. I was thinking that providing a mechanism to allow regular users to share directories that they own might be useful. I also think that there should be an option for the sys. admin to enable/disable this option.

I think that the windows network wizard should be a target, it could be used to generate the conf file with added details.  I am going to mock up a sample interface when I get a chance which could be a good discussion point.

(if someone can pm me with a quick way to make interfaces examples without having to resort to photoshopping existing windows)

---

### Post by ghoseb on 2006-04-30
Hello guys! First of all thanks a lot for reading my spec and commenting on that. Your suggestions have been indeed awesome. I have never used Windows, so the GUI was a bit unclear to me. But now I have a clear picture of how it should be.
I am going to propose this project as a part of Google Summer of Code 2006, I hope the Ubuntu folks select it :)
troyDoogle7, it's pretty easy to create mockups if you know a bit of glade and pygtk. The screenshot in the spec was created by me in < 20 mins.
What I can say is that I really liked all your suggestions and the features you guys have suggested will surely be in the final product. I am going to make changes to the spec itself to reflect what you guys have suggested. More mockups of the wizard will come soon.
You guys rock!
Thanks again,
BG

---

### Post by ghoseb on 2006-04-30
Hey guys, I have added mockups of the wizard interface in the spec. Kindly check it out and comment on it. [https://wiki.ubuntu.com/GUISambaConfigSpec](https://wiki.ubuntu.com/GUISambaConfigSpec)
Thanks :)

---

### Post by troyDoogle7 on 2006-04-30
Hi ghose, 

Thanks for the message.  If you need any assistance regarding any aspects from windows, I am microsoft certified and can help with any aspects you need.

I haven't played with glade etc, but I started putting together a php based web ui generator. Which would allow me to make menus etc like you producted.  

It would allow us to have a good way of showcasing the ui suggesetions and deciding whats best.  Its also xml based but I have simplified the tags so that its really easy to generate just using notepad

Here is the sample I created from a small text file : 
> <title> Samba Configuration Editor</title>;
<menu>file,edit,help</menu>;
<icons></icons>;
<buttons>Add,Delete,Preferences</buttons>
<table>;
<th>Directory,Permissions,Descriptions</th>
<tr>/home/jane/work, Read-Write, Janes Work Space</tr>
<tr>/dump,Read-write,Place for Dumping files</tr>
</table> 

Which produces this: 
[www.cherrysupport.com/guiml](www.cherrysupport.com/guiml) 

I am going to dev it further so that we have more intelligence built into the engine and it can do other menu types as well.

---

### Post by ghoseb on 2006-04-30
troy, 
Your idea is cool! I guess you are doing this with screenshots broken down into different widgets and then assembling them as required. This is useful for doing quick mockups may be. Glade on the other hand is a programming tool. It makes the programmers job easier.
Anyway, have you seen the screenshots of the wizard interface? Are they okay?
Regards,
BG

---

### Post by troyDoogle7 on 2006-05-02
Hi Ghose, I have an alternative wording however I am going to build a template so its easy to explain.

---

### Post by Ozitraveller on 2006-05-02
Would this need to integrate with the Network Manager in Gnome? Or GTK Wifi Project ?

---

### Post by bugme on 2006-05-06
Hostname is set up in the Networking dialog and should not reconfigurable in Samba dialog, because of redundant configuration.

Although CIFS provides an own naming system using WINS, Microsoft decided in Windows XP to use the same hostname for DNS and CIFS afaik. Dealing with different names for the same machine seems not very intuitive, so Microsoft provides only one dialog for seting up the name.

---

### Post by dyssident on 2006-06-10
i totally agree on the need for this. ive been experimenting with a prototype for about a week now and ive found that ensuring it will Just Work its not as straight forward as i had expected. here are some thoughts for discussion:

1. in the interest of Just Working, it seems useful to define one standard setup and allow minor variations. 

the standard setup would need to find a balance between security and ease of setup. for instance, for most firewalled home networks you could simply allow anonymous read-write access to all shares. this would be allow the easiest use possible,  but its not a good idea because it is after all the most insecure setup possible.

security = user
guest ok = no
browseable = yes
read only = yes/no
*user must supply allowed users but gui will automatically add them to smbpasswd and passwd if needed

another idea would be to sacrifice security for ease of setup:

security = share
guest ok = yes
browseable = yes
read only  = yes/no
force user/group = userX

in this instance, they user would only ever have the choice between creating shares that everyone could read or everyone could read+write.

choosing a standard configuration would also eliminate the need for the No User Authentication/User Must Log In choice (ie. 'security = share/user). a person that needs this gui most likely isnt going to have a domain controller. or perhaps user security doesnt work with Win95/98?

2. samba automatically exposes a share of the home directory of username that the client has connected with. i have a feeling that this may actually encompass alot of use cases. should this feature be made obvious in the gui?

3. if you want the gui to Just Work, you have to think about rwx permissions on the files themselves. should the gui do a quick check in the share folder for r-- or rw- (depending on shares 'read only' param) and offer to set permissions if they are inadequate?

---

### Post by dyssident on 2006-06-26
just want to bump this thread and see if anyone out there has any ideas cooking.

---

### Post by leibowitz on 2006-06-27
Yup, I'm currently working on some tools to configure Samba easily, but can't find any revelant information on how to present it to the user. As it was said before, 
[https://wiki.ubuntu.com/GUISambaConfigSpec](https://wiki.ubuntu.com/GUISambaConfigSpec)

the gui should be simple to use, and complete to handle advanced configuration. 

I've done some basic C code to scan the config file, and setup values/ delete entries / comment properties / etc. This is called "libsmbparse" Don't know if the name is already used.

I don't know really where it should end, maybe the library should be really constructed as a library, but is not yet. Then, it will be used by some GUI to construct and edit samba configuration file.

By now I've implemented the library in an ncurses based tool, presented like a wizard. But it's not fully implemented. 

You get the choice to build a :
PDC, Member Server, Domain Client, or a Workstation in a Workgroup.
The only one done right now is Workstation in a Workgroup. 

Of course you can download the code at the bottom of this webpage. 
[http://boby.joe.free.fr/libsmbparse/SambaConfigLib.html](http://boby.joe.free.fr/libsmbparse/SambaConfigLib.html) ** Informations**

Talking about the GUI now.

I was thinking to build a wizard like GUI. But that's not the purpose of this message. It is more about a powerfull samba config editor, as you said here, that is necessary. First I thought about a gui presenting the config file per section, as you can see there; and don't get confused by the window borders.
[http://boby.joe.free.fr/libsmbparse/GUI-Mockup/mainSambaConfig.JPG](http://boby.joe.free.fr/libsmbparse/GUI-Mockup/mainSambaConfig.JPG) Old Screenshot

But It's not a good idea I think we could do better. That's why I'm here. I will be creating a new GUI mockup by tomorrow or even before. And will be waiting for your feedback on the future mockup.

Edit: here it is. Any comment would be welcome.
[http://boby.joe.free.fr/libsmbparse/GUI-Mockup/gui-network-sharing_window.png](http://boby.joe.free.fr/libsmbparse/GUI-Mockup/gui-network-sharing_window.png) **Screenshot**

Edit2: There is one more window. This is the "Shared Folders" extended.
[http://boby.joe.free.fr/libsmbparse/GUI-Mockup/gui-shared-folders_window.png](http://boby.joe.free.fr/libsmbparse/GUI-Mockup/gui-shared-folders_window.png) **Screenshot**

Edit3: link to the .glade project.
[http://boby.joe.free.fr/libsmbparse/NetworkSharing-GUI_only.tar.bz2](http://boby.joe.free.fr/libsmbparse/NetworkSharing-GUI_only.tar.bz2) **TAR.BZ2 Glade file**

---

### Post by dyssident on 2006-06-27
Im inclined to make wizards braindead easy and then provide every option under the sun in the full app; the wizards should remain easy to trigger in case the novice user gets themselves into trouble with the advanced options. Using this style, you get the best of both worlds, a fully featured gui for advanced users and a super quick setup for home users that just want to share their mp3s. Im inclined to totally leave domain and active directory out of the wizard, because if you need one of these, you are not an average home user and therefore dont need a wizard, or a gui for that matter.

I would like to see the options the user has in the wizard limited to the few most commonly used ones. they would be presented in descriptive, non-technical terms.

Step 1
How would you like to share your files
- Everyone on the network can read only
  Choose this for a document server with information you dont want changed
- Read+write restricted by a single password
  Good for small workgroups
- Read+write restricted by individual user accounts
  This is the most secure, but you will have to manage your users
- Everyone can read+write 
  Everyone on your network will have open access to your files.
  This should ONLY be used on a secure, firewalled home network. 

Step 2
- Hostname, Workgroup

Step 3
Collect information dependent on choice in Step 1 i.e. share password or grid to enter users

After clicking 'Finish' user will be dropped into main application which would look something like the Gnome Shared Folders manager. Ill do some screenshots of the prototype Ive been working on and post them later, but the main app interface is a simple tabbed setup. Tab 1 looks very much like Shared Folders, Tab 2 is Samba specific options. The non existent Tabs 3 and 4 could concievably be NFS and SSH specific options.

Btw, there are two things in the Shared Folders app that I really like and I think are worth immitating: 1. it offers to install samba or nfs if you dont have either 2. It handles nfs and samba shares with the same interface

There is at least one more issue that needs to be considered. No matter what security mode you use, you are still subject to the permissions set on the individual files and directories. In order to ensure that it Just Works, it may be necessary to check permissions on shared files any time a share is created.

---

### Post by dyssident on 2006-06-27
[QUOTE=leibowitz]
And will be waiting for your feedback on the future mockup.
[/QUOTE]

My prototype is done in quick and dirty Perl; I use a package called File::Samba that very much sounds like your libsmbparse. You may want to look through File::Samba on cpan for some ideas, but it already sounds like libsmbparse is more fully featured.

Very good work on the second and third screecaps. The first isnt very different from just hand editing the smb.conf. The good thing about a gui is it reduces complexity by only presenting some options and eliminating conflicting options. I like the name of the first one "Samba Facile"; thats one of those great words that means the same thing in many languages.

What I would change on the second one, which I presume is the wizard, is instead of a simply checkbox for sharing, I would give the descriptive options that I ennumerated in my previous post. Since Samba has several different security modes (ie security = share, security = user) and the user should have some easy, nontechincal way to choose between them.

For third screencap (Im presuming its the full app) I would use a tabbed interface as I described in the previous post. This would present a super simple, non-intimidating share creation interface (your "shared folders list") with the ability to hit the next tab and get the "[global]" configuration options (your "Global parameters").

Also, since setting "security = share" allows you to put a single password on each share, adding this password should probably be part of the "add share" dialog. If I remember correctly, you can set most security related options (everything but security = *) in both globals and in the share specific section, so maybe it would be reasonable to supply security options for globals configuration and allow them to be overriden when you create a share. The samba configuration file paradigm seems to support this "define in globals, override in particular shares" idea.

---

### Post by LordHunter317 on 2006-06-28
I have a few comments to make, in no particular order, and not address at anyone, even when they should be:[list][*]**Do not support security=share in any way, shape or form.**  It's barely supported upstream, it will go away eventually, and it makes life for everyone harder.  Just pretend it doesn't exist.  Don't do anything to accomidate it.[*]You need to very careful think about what options are exported and how.  For exampe, none of the netbios naming or scope options should likely be exported *ever*.  The few users who need to play with them won't be using this GUI.  There are lots of options for Samba that apply to essentially unique configurations or deprecated Windows setups.  They shouldn't be bothered with in the tool. [*]Share exportation really shouldn't be done thorugh this tool.  The right way is to extend nautlius with the ability to add shares and configure them (i.e., exactly how Windows does it).  That's the more usable option, IMO.  However, starting with the per-share configuration here isn't a terrible thing to do, since that sort of thing takes time to develop and it's eaiser to develop it as part of this then as a nautilus extension[*]You need to support Windows domain configurations, including as a workstation.  It's unacceptable not to.  The problem is being smart about it: selecting LDAP/K5 over Winbind when appropriate and such.  You could probabyl ask them for the details to be capable of querying AD and then just query to see if the proper object types are available.  If so, use LDAP and K5.  If not, use Winbind.  This is unfortunately icky.[*]If you boil the sharing down to security templates, include the ability to easily customize the security settings on a per-share basis.  Don't forget filesystem permissions play a role as well.[*]There's a bunch of per-share options that should probably be ignored as well (like all the force options).[*]Don't forget printing, which is a can of worms I have not the  energy for, ATM.[/list]

---

### Post by dyssident on 2006-06-28
> **LordHunter317]
**Do not support security=share in any way, shape or form.**  It's barely supported upstream, it will go away eventually, and it makes life for everyone harder.  Just pretend it doesn't exist.  Don't do anything to accomidate it.
[/QUOTE]

I would be perfectly happy to see "share" thrown out, assuming that win95/98 boxes work correctly with "user." (I seem to remember hearing of some problems, but I could be wrong) Not only is it the Samba default, it was a joke to begin with and ignoring it only makes the gui simpler.

[QUOTE=LordHunter317]
You need to very careful think about what options are exported and how.  For exampe, none of the netbios naming or scope options should likely be exported *ever*.  The few users who need to play with them won't be using this GUI.  There are lots of options for Samba that apply to essentially unique configurations or deprecated Windows setups.  They shouldn't be bothered with in the tool.
[/QUOTE]

Im always down for simplifying options said:**
> 
Share exportation really shouldn't be done thorugh this tool.  The right way is to extend nautlius with the ability to add shares and configure them (i.e., exactly how Windows does it).  That's the more usable option, IMO.  However, starting with the per-share configuration here isn't a terrible thing to do, since that sort of thing takes time to develop and it's eaiser to develop it as part of this then as a nautilus extension


I cant wait for Nautilus to support exporting shares, but until it does, I think setting up shares indespensable.

[QUOTE=LordHunter317]
You need to support Windows domain configurations, including as a workstation.  It's unacceptable not to.  The problem is being smart about it: selecting LDAP/K5 over Winbind when appropriate and such.  You could probabyl ask them for the details to be capable of querying AD and then just query to see if the proper object types are available.  If so, use LDAP and K5.  If not, use Winbind.  This is unfortunately icky.
[/QUOTE]

Im not morally opposed to handling domains and AD, but we should consider who this is tool is aimed at, namely the home user. Joe Windows is highly unlikely to have a domain on his home network, and if he does, hes good enough at least not to need a wizard. Hows that for a catch 22?

[QUOTE=LordHunter317]
If you boil the sharing down to security templates, include the ability to easily customize the security settings on a per-share basis.  
[/QUOTE]

My inclination is to have the wizard set up global options and the share add dialog specify share specific options. The user should expect that whatever he sets up in the wizard, say a globally accessile read only server, any subsequently added shares should behave that same way. This would be accomplished by setting the necessary defaults in globals.

The user would then of course have the option of having a given share behave differently by specifying different options when creating it.

[QUOTE=LordHunter317]
Don't forget filesystem permissions play a role as well.
[/QUOTE]

I have a feeling this will turn out to be the greatest enemy of Just Working.

[QUOTE=LordHunter317]
There's a bunch of per-share options that should probably be ignored as well (like all the force options).
[/QUOTE]

I agree that anything that can be ignored should.

[QUOTE=LordHunter317]
Don't forget printing, which is a can of worms I have not the  energy for, ATM.
[/QUOTE]

Better to fight that battle another day.

---

### Post by leibowitz on 2006-06-28
as LordHunter said, two parameters should be taken into consideration when making the samba configuration software. 

First is the Active Directory domain Joining. I would mostly copy/paste the authconfig tool from Red Hat as someone proposed, and I think that he is porting the utility on Ubuntu already (seen mailing list messages about it but don't know where he is atm). 
For more informations about Active Directory Client with Samba/Winbind, visit the wiki.
[https://wiki.ubuntu.com/NetworkAuthentication](https://wiki.ubuntu.com/NetworkAuthentication)

And the Second one, and last, is the print sharing. It is almost everything. If you cannot share your printers on the network with it, then it's prety useless, as the share-admin tool is.

If we take both in an utility that is confortable, easy, and that is prety what you dyssident described, then we have something.


Edit: I've updated the screenshots about the GUI tool, and have implemented it in a binary, with the smbparse code aswell. 
[http://boby.joe.free.fr/libsmbparse/gui.html](http://boby.joe.free.fr/libsmbparse/gui.html) **Nothing real started yet.**

---

### Post by dyssident on 2006-06-28
> **leibowitz]
First is the Active Directory domain Joining. I would mostly copy/paste the authconfig tool from Red Hat 
[/quote]

Sounds great said:**
> And the Second one, and last, is the print sharing. It is almost everything.


Agreed; on a second look at the docs, once youve got folder shares working adding the needed code for doing printing appears pretty trivial. Cant think of any reason not to do it.

Nice work on the screenshots; once I make it home Im going to give the code you posted a go. Ive posted a few of my ideas here 

Edit: [Screenshots]("http://www.voxpopulimedia.com/pub/sambagui/screenshots.html")

I apologize for the overwhelming lameness of using scanned drawings, but Im on campus and am thus surrounded only by locked down Windows machines. As soon as I get home Im going to have to get back to hacking and post some screen shots so I dont get totally outclassed.

---

### Post by LordHunter317 on 2006-06-29
> **dyssident]I would be perfectly happy to see "share" thrown out, assuming that win95/98 boxes work correctly with "user."[/quote]They do, as well as they will.  They don't work well period, so I'm not sure that's really a worrysome concern.  Even MS' answer was more or less always, "Move to NT".

> Im always down for simplifying options said:**
> It shouldn't even be set.  It defaults to being correct.  IF you set it and they change the hostname in the future, it will be wrong in the future.

[quote]Im not morally opposed to handling domains and AD, but we should consider who this is tool is aimed at, namely the home user. Then it should have wider scope.

[quote]I have a feeling this will turn out to be the greatest enemy of Just Working.Most likely, yes.

[quote=leibowitz]I would mostly copy/paste the authconfig tool from Red Hat as someone proposed,[/quote]Please don't.  It's utter broken buggy crap.

---

### Post by leibowitz on 2006-06-29
> **dyssident]Do you have much experience with AD?[/QUOTE]

Yes, Pretty much. 
I studied Microsoft Windows 2000 Server, aswell as 2003 six months ago. And it was deeply about Active Directory. 

Talking about copying authconfig tool from Red Hat
[QUOTE=LordHunter317]Please don't.  It's utter broken buggy crap.[/QUOTE]
Yes, it is. I've tried to join a domain with authconfig said:**
> http://www.redhat.com/archives/fedora-config-list/2006-April/msg00016.html[/url]

I also think that it would be time consuming to recode all this part. Maybe we should try to help in fixing Red Hat code.

Talking about "netbios name"
[QUOTE=LordHunter317]
It shouldn't even be set. It defaults to being correct. IF you set it and they change the hostname in the future, it will be wrong in the future.
Not if you've set "netbios name = %h". That should be the default imho.

As already said, the netbios name should be fixed to the hostname so, as In Windows, the user is not presented with more than one hostname configuration.

---

### Post by dyssident on 2006-06-29
[Here are some quick screenshots]("http://www.voxpopulimedia.com/pub/sambagui/screenshots.html")

[Here is the code]("http://www.voxpopulimedia.com/pub/sambagui/wxSamba.20060629.tar.gz") done in wxWidgets and Perl for no other reason than thats what Im fastest with.

---

### Post by leibowitz on 2006-06-29
I like your idea of presenting the role of the computer; Standalone Server in your case; that it has on the network. Also the "Run Setup Wizard" button that comes with it. I think that's pretty cool.

But something seems troublesome, that is the duplicate entry for users rights. Why do we have to present two users properties, one that is global for everyshare, and one for each share. Should'nt it be more simple for the user to get only one, for each shares. So **why is the global user setup needed**?

PS: that's something I have thinked about, but it's not yet. So it's just an idea. What do you think about it ?

---

### Post by dyssident on 2006-06-29
> **leibowitz]I like your idea of presenting the role of the computer said:**
> 

Thanks much. My assumption with the wizard is that it primarily configures global only parameters.

[QUOTE=leibowitz]
But something seems troublesome, that is the duplicate entry for users rights. Why do we have to present two users properties, one that is global for everyshare, and one for each share. Should'nt it be more simple for the user to get only one, for each shares. So **why is the global user setup needed**?


Its not obvious in the screen shot, but there is only an option to block users in the global context. This idea comes from the Oreilly samba book: they recommend explicity putting system users in [global] 'invalid users' (ie invalid users = root, daemon, wheel etc...) as an added security measure. 

You are right that it is is not strictly necessary and potentially confusing. We could just as easily set 'invalid users' behind the scenes and not give the user the option of changing it in the gui.

A note on the scope of wizards:

My assumption is that the wizard should only set [global] parameters, with maybe the option of creating the first share at the end. If we add global options that directly affect shares to the wizard (ie. guest ok, read only) , reruning the wizard after shares have been created will change the behavior of those existing shares if they simply depended on the default global values.

If we gave the option of a standalone world accessible read-only server, smb.conf would end up looking like:

```

[global]
security = user # default
guest ok = yes
guest account = ftp
guest only = yes
writeable = no

[share1]
path = /export/share1

```

then if we reran the wizard and chose a user account restricted standalone, smb.conf would look like:

```

[global]
security = user # default

[share1]
path = /export/share1

```

At this point, share1 behaves totally differently than in the first case. It has stopped accepting guests and the server will now demand a username/password to connect to the server. So it may be that setting share parameters in [global] is not a good idea at all. Any thoughts on this?

---

### Post by LordHunter317 on 2006-06-29
I would not change the guest account from 'nobody', if it were me.  That will only add to the confusion.  

If you refuse to use that, at least create a samba guest account.

---

### Post by dyssident on 2006-06-30
After a long night of nothing to do, Ive made some updates to my prototype: [wxSamba.20060630.tar.gz]("http://www.voxpopulimedia.com/pub/sambagui/wxSamba.20060630.tar.gz")

It will allow you to some rudamentary share creation and step through the half-finished server setup wizard (which does nothing). If you run it via './wxsamba' it will sudo and can potentially mess up your smb.conf, so be sure to back up.

---

### Post by dyssident on 2006-07-01
You can define 2 'magic' shares in smb.conf: [printers] and [home]. If you request an undefined share, assuming that [printers] and [home] are defined, samba does the following:
1. if the share is a users name, authenticate them and connect them to their home directory
2. if the share is a name of a printer defined in /etc/printcap, authenticate them and connect them to the printer
3. use default share; not important for the issue at hand

Assuming that we will always have [printers] and [home] defined, should we show all of the homes and printers (ie printers in /etc/printcap and users in /etc/passwd) in the shared resources list?

The reason that this could be useful is that I expect users to often want to share home directories and printers theyve previously set up. Showing them that homes and printers are shared by default could serve to flatten the learning curve and save some time. Any thoughts?

---

### Post by leibowitz on 2006-07-01
Good question. I don't have an answer, only thought.

I don't think you should be listing homes and printers share, because they are "special" section. It is an advanced configuration that should be presented maybe in the wizard, when a system administrator want to setup a File Server for Home directories, or a print server.

For the print sharing, a checkbutton is sufficent imho. And for Home directories, maybe too. At least that is what they have done in Suse Linux Enterprise Desktop 10, when you setup a domain client, there is a checkbox:
_ Create personnal home directories 

It is probably using pam_mkhomedir. But that's linux client in a domain. What you want to do is creating homedir shares, right ?

Then it should be in the shares, but if you were listing it as a normal share, it would be confusing to the user. What's the difference between both ? 

It's just not the same. Also you should be asking yourself "what is needed to configure home directories". I don't think many option should be customisable, because I don't have an idea of what is needed. 

Here is a smb.conf file from the Suse Linux Enterprise Desktop 10 setup in a domain, as a client. The revelant part is the "homes" section. Also do not forget that this is to enable logon localy with a domain login/password. 

```
# smb.conf is the main Samba configuration file. You find a full commented
# version at /usr/share/doc/packages/samba/examples/smb.conf.SUSE if the
# samba-doc package is installed.
# Date: 2006-06-16
[global]
	workgroup = BOBYJOE
	printing = cups
	printcap name = cups
	printcap cache time = 750
	cups options = raw
	map to guest = Bad User
	include = /etc/samba/dhcp.conf
	logon path = \\%L\profiles\.msprofile
	logon home = \\%L\%U\.9xprofile
	logon drive = P:
	idmap gid = 10000-20000
	idmap uid = 10000-20000
	realm = BOBYJOE.HOMELINUX.COM
	security = ADS
	template homedir = /home/%D/%U
	template shell = /bin/bash
	winbind offline logon = yes
	winbind refresh tickets = yes
[homes]
	comment = Home Directories
	valid users = %S, %D%w%S
	browseable = No
	read only = No
	inherit acls = Yes
[profiles]
	comment = Network Profiles Service
	path = %H
	read only = No
	store dos attributes = Yes
	create mask = 0600
	directory mask = 0700
[users]
	comment = All users
	path = /home
	read only = No
	inherit acls = Yes
	veto files = /aquota.user/groups/shares/
[groups]
	comment = All groups
	path = /home/groups
	read only = No
	inherit acls = Yes
[printers]
	comment = All Printers
	path = /var/tmp
	printable = Yes
	create mask = 0600
	browseable = No
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/drivers
	write list = @ntadmin root
	force group = ntadmin
	create mask = 0664
	directory mask = 0775
```

---

### Post by dyssident on 2006-07-02
[QUOTE=leibowitz]
I don't think you should be listing homes and printers share, because they are "special" section. It is an advanced configuration that should be presented maybe in the wizard, when a system administrator want to setup a File Server for Home directories, or a print server.
[/quote]

The way I understand it is that [homes] and [printers] are set by default because, at least for the home user, they cover a good part of the usage cases.

When I first started using Samba, the first thing I did is share my home directory. I expect that most home users will, like me, primarily want to share their home directory and not know that samba will do it automatically. Starting up an application to do something and seeing clearly that its already being done for you is the ultimate in convenience.

[QUOTE=leibowitz]
For the print sharing, a checkbutton is sufficent imho. And for Home directories, maybe too. 
[/quote]

A checkbox is a good idea, because at least for homes there is really only one setup you generally want to use.

[QUOTE=leibowitz]
What you want to do is creating homedir shares, right ? Then it should be in the shares, but if you were listing it as a normal share, it would be confusing to the user. What's the difference between both ? 
[/quote]

I dont actually want to create any specific shares, just show the user which home directories and printers samba is already automcatically sharing by virtue of [homes] and [printers] being set.

It would go something like this: on startup, see if [homes] is defined. If so, figure out which home shares Samba will autoconnect to when an unknown share is requested. Display those virtual home shares to the user as real shares by making entries in the gui's shares list. This will have the effect of letting the user know that samba is already automatically sharing the displayed homes directories; so the main idea is to unambiguously show the user what is being automatically shared for them.

---

### Post by leibowitz on 2006-07-03
Good.

If you can do it, it should be done. Anyway it seems difficult. 

Also I wanted to post a link to the gsambad utility, that is GPL, but should not be replicated. Because it is exactly what the final GUI should _not be_! GSambad is probably great in the eyes of his creator, but I doubt anyone here will have a nice user experience with it. Anyway, maybe some code could be reused.
[http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=16&Itemid=30](http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=16&Itemid=30)

---

### Post by dyssident on 2006-07-05
[QUOTE=leibowitz]
Because it is exactly what the final GUI should _not be_! 
[/QUOTE]

Id be interested in any specific criticisms you have of it.

I agree that its a great example of bad gui design. Instead of reinterpereting the configuration options for the user, its built around a one for one correspondence between configuration fields and gui text boxes, so its not significantly different than editing the config file by hand.

Ive posted the latest prototype here: [wxSamba.20060704.tar.gz](http://www.voxpopulimedia.com/pub/sambagui/wxSamba.20060704.tar.gz). Read INSTALL for sketchy instructions on getting it to run.

---

### Post by edlentz on 2006-07-05
I wonder if there is a GUI for Samba on a network of XP machines yet.  I am a novice and I need something easy to install and administer.  If possible, without needing to sit at the server.

Thanks alot!

---

### Post by dyssident on 2006-07-06
[QUOTE=edlentz]I wonder if there is a GUI for Samba on a network of XP machines yet.  I am a novice and I need something easy to install and administer.  If possible, without needing to sit at the server.[/QUOTE]

Unless youre using an ancient version of Win95, the windows machines connecting to samba really dont matter much. 

If you just want to share some files on your linux box via samba, the Shared Folders gui that comes with Ubuntu is pretty serviceable. You should start a new thread describing in detail what youre trying to do and youll get lots of advice.

---

### Post by edlentz on 2006-07-06
Thanks Dysidant I'll look into it!

---

### Post by saracen on 2006-07-27
What's the status on this tool?

---

### Post by dyssident on 2006-07-28
> **saracen said:**
> What's the status on this tool?

still slowly working on it.. i havent been able to drum up as much interest as id hoped,, so progress has slowed down..

i have basic share creation and permission setting working.. stand alone server wizard works (but it naturally doesnt do much).. all default shared home directories and printers are shown in the gui..

currently im throwing out wxWidgets and redoing the gui with GTK,, so that is taking some time..

next step is real printer configuration support..

in short,, its still alive,, but it isnt usable.. if you are interested,, i could use some input on the current state of things..

---

### Post by saracen on 2006-07-28
Are you using python or C for GTK?

---

### Post by neveceral on 2006-08-09
Will it be possible to use your GUISamba for setting up folder sharing between local ubuntu users? Because it is almost impossible (look [here]("http://www.ubuntuforums.org/showthread.php?t=145741") and [here]("http://ubuntuforums.org/showthread.php?p=1352866")).
I set up the permissions for group of users for "pub" sharing folder, but there was a problem, that i had to set up it manualy for every created subfolders, because the new subfolders didn’t inherit (?) the permissions from parent folder. Then i tryed to solve this problem with some scripts recursively changing permissions of folders and files, but this solution has many limitations too.
So i think, that the best solution is using GUISamba.

---

### Post by ShinjiLeery on 2006-12-30
I hope this project isn't abbandoned... It's very important for usability, have a Graphical Samba configuration tool...

---

### Post by thenebcouk on 2007-02-12
Hi all, just checking up on this tool.
I'm kinda semi-working on something similar, a tool called scMount - ie simple cifs mount.
Currently just made it for easier newbie mounting at our university network but might be looking into more development for a more general tool with config file in the future, so might be better just to work on this project.

Current early alpha: [http://www.theneb.co.uk/scMount.tar.gz](http://www.theneb.co.uk/scMount.tar.gz)
On launchpad too.

---

### Post by gurgle on 2007-04-12
this is so overdue its not even funny.

---

### Post by gaten on 2007-04-12
This is a great project and I hope it doesn't die. I have one suggestion that may or may not be outside the scope of this tool:

[U][B]The Devil You know...
[/B][/U] If an (above) average Windows user knows how to share a folder, they probably know one way and one way only. Right click on the folder, select "Sharing and Security", and go from there. As Nautilus already emulates that, this tool could extend the functionality of the "Share" option by adding (replacing?) the advanced options presented by the tool. At this point, when you decide to share a folder through Naut, you have a variety of options when you decide to share the folder, however there are ALOT more options available under Samba. Bringing the availability of those options to an "advanced" tab or some such in the sharing windows would be great. 

I defiantly like the idea of a central share management GUI, that would greatly simplify things. Thanks for doing this once again

---

### Post by thompa on 2007-05-15
Just like to add my weight to this.
I am not a computer newbie... but each time I have updated to another version of Ubuntu, I have had a problem with Samba. The trouble is that once it is set it works - so I forget how I did it when I upgrade and have to go through the frustration again of sharing printers and folders.
Sharing should be easy and a wizard should run at installation. Another problem that I have is with my wireless usb connector which is persistently reluctant to be recognized. If some way of improving wireless detection could be included, this would be great!

---

### Post by Qu4k3R on 2007-10-18
I've searched with google something about: "system-config-samba"
I found the GUI for the samba (system-config) app.

And I get this.

[http://packages.ubuntu.com/gutsy/admin/system-config-samba](http://packages.ubuntu.com/gutsy/admin/system-config-samba)
You'll find there the debian packages..
But I'm not sure if it is only for gutsy..

I am trying to install it.

Thanks to you all..

---

