---
title: "Disturbing trend - GUI-only configuration? Text files cryptic?"
date: 2006-10-16
forum: The Cafe
---

### Post by Charles Hand on 2006-10-16
I'm an old fart. I worked for a coupla decades with a Sun workstation on my desk. I tried to adopt Linux for my personal computers three times. This last time it stuck.

But I'm seeing a disturbing trend. The last time I used Linux was in the 2001-2002 timeframe. At that time, everything was still ultimately configured with text files, and it wasn't too hard to figure out where a configuration file was, and it wasn't too hard to figure out what the entries in the file did (most often, the configuration files were generously commented).

But with Nautilus/Metacity and now Beryl I'm starting to see this gui-only configuration philosiphy. Configuration files are hard to locate and when they are located they have obscure names. Gnome has two layers of intervention between the user and the configuration file: the gui and then conf-editor. If you do open a configuration file, the xml code and naming inside is usually arcane and uncommented. Dependencies are hidden.

Is Linux configuration destined to become just like Windows?

---

### Post by meng on 2006-10-16
Funny, many would argue that the old way of configuring things is bad, and would applaud the move to GUI-dominant configuration. Funny how tastes differ.

---

### Post by Rackerz on 2006-10-16
Because I'm not such a poweruser when it comes to Linux, the gui way of doing things is better for me and it needs to be like that if Linux is going to gain any progress.

---

### Post by coder_ on 2006-10-16
I prefer having the old way too.  More fun ;)

---

### Post by Charles Hand on 2006-10-16
I misrepresented myself. I'm not AGAINST gui configuration. I'm just saying that a strength of Linux has always been that the gui configurators work on text files. Thus, there is always a basic, consistent level at which you can configure things that the gui doesn't let you do, or automate configuration using scripts. It's all part of having control under the hood when you want to, which is a primary difference between Linux and Windows.

---

### Post by DoctorMO on 2006-10-16
I agree, the openness must always extend to the configuration files and it's important that every configuration you do in a project is well documented.

I document all mine, especialy the xml configs which are always made with text editing in mind.

---

### Post by vbt on 2006-10-16
I'm still a noobie with linux. I chose Ubuntu because it was an easy transition for me after a gazillion years on MS.  

Right now I can do everything I need to do on the computer and I'm happy with Ubuntu and Gnome. An OS without a GUI would have kept me away from linux. And I'd still be dealing with patches and anti-this and that.

My 2 cents...

---

### Post by BWF89 on 2006-10-16
@Charles Hand: Doesn't Slackware make you edit things the old fashioned way?

---

### Post by desmondo on 2006-10-16
I agree with the OP.

Having a GUI to configure an application is a great tool, and having a text file to configure an application is also a great tool.  There is no reason the same application can't support both methods, and it's a shame when an application doesn't support both.

---

### Post by Charles Hand on 2006-10-16
Is this thing on?

I'm not against GUI.

---

### Post by Tomosaur on 2006-10-16
I agree that there is what appears to be a disturbing level of complication with certain GUI centric things, and prefer having my config stuff easily accessible and editable through the command line.

---

### Post by vbt on 2006-10-16
Sorry, I was away from the computer for a while after writing and I saw your comment about not being against GUI after I submitted mine. 

This reminds me of my parents arguing over something until I told them they were saying the same thing, LOLOL!

---

### Post by Polygon on 2006-10-16
even though there is a lot more tools to configure stuff with the GUI nowadays, there is nothing stopping you from opening gnome-terminal and editing any configuration file you want with nano or whatnot :D

---

### Post by zenwhen on 2006-10-16
If you give me a tool to configure options on my OS and do not provide me a readable plain text way to deal with those settings, then you have not provided me anything but a layer between me and functionality.

What happens when your GUI tool breaks? What if I want to configure your application or setting remotely without super slow x forwarding?

I am out of luck. 

I am pointing the finger at application developers who do not provide access to well commented configuration files.

**YOU** are destroying one of Linux's main advantages. Please think about the GUI user and the user who can live without a preference pane for every setting. Think about the people who will not be able to properly use your tool if you hide every setting within a tab on an advanced settings menu.

---

### Post by Moeru on 2006-10-16
Newbie or not, I don't see this as a disturbing trend. I view it more as a stepping stone or a stumbling point in a way. Since I've been interested in *nix, I've always heard the cry of "Be ready for the desktop!" or the same concept in different words. To developers, this is frustrating because they are used to Terminal. People want GUI. They want the "ease" of Windows they know and love. This forces the developers to lean towards that. Sometimes, people lose sight and bad things happen. I'm willing to give them the benefit of the doubt for a bit. Besides, isn't Linux the most configurable OS? The ones who want it both ways will find a way.

---

### Post by emarkay on 2006-10-16
> **Charles Hand said:**
> Is this thing on?
I'm not against GUI.

Dude, you have to bang it 'till you hear feedback!

One oldster to another...

Yes, knowing what goes on behind the window or the gooey is good.  Yes, it is getting hard t o see what is being done while the progress bar moves to the right. Ubuntu seems (IMHO) to be an almost "dumbed down" (and I don't mean that in my usual derogitory stance - just that a lot is hidden) transistion between us Windows For Workgroups 3.1 to WinXP slaves to the wonderful world of  Linux.

I see "Distributions matched: 298" versions of Linux now:
[http://www.linux.org/dist/list.html](http://www.linux.org/dist/list.html)
For example:
Ubuntu 6.06.1, SUSE 10.1, Fedora Core 5,  
SimplyMEPIS 6.0, Mandriva 2007, CLinuxOS 0.93a, Damn Small 3.0.1, Debian 3.1r3, Slackware 11.0, Knoppix 5.0.1, Gentoo 2006.1, FreeBSD 6.1 ...

Surely one can find the sane balance between gooey gumbdrop and serious work from those variants...

IMHO single source sucks, but  200 sources suck, too!

---

### Post by IYY on 2006-10-16
I have no time to write a full reply, but I pretty much agree with the original poster. GUI tools are nice, as long as they are compatible with the existing command line tools. If I edit something via command-line, the GUI should detect that, and if I edit something in the GUI, the output in the conf file should be easy to understand and/or modify. Otherwise, we're *almost* as bad as Windows/OSX (not quite as bad, because at least here we have the choice to ignore the GUI tools and use only the command line, and that will never be taken away from us).

---

### Post by Kindred on 2006-10-16
I haven't noticed this trend but it would perhaps concern me if I did.  So far i've seen nothing to worry about though I must say.

---

### Post by aysiu on 2006-10-16
You're talking about Gnome's confusing XML files? Just use IceWM. All the config files are text files in one folder, and they're really easy to manipulate.

---

### Post by Charles Hand on 2006-10-18
> **aysiu said:**
> You're talking about Gnome's confusing XML files? Just use IceWM. All the config files are text files in one folder, and they're really easy to manipulate.

Thanks for the tip. Interesting window manager. Fast, too! It still uses the old clunky fonts, but I'll play with it.

---

### Post by bonzodog on 2006-10-18
I have to admit to being an old fart on this one, too; 
I switched to Zenwalk, a derivative of Slackware after getting fed-up with all the GUI tools. I like the CLI and config files. 
 Maybe you would feel more comfortable in a more 'advanced' distro?

Try Slack 11, Zenwalk 3.0, Arch linux, to name but a few....

---

### Post by darkhatter on 2006-10-18
Which apps only have gui-only tools, I haven't seen any

---

### Post by Demio on 2006-10-18
Do you guys even read his posts?

He's complaining about the obscurity in some config files (eg.: the ones in GNOME and Beryl). 

They are editable by text but not either nicely commented or very readable.

---

### Post by desmondo on 2006-10-18
> **darkhatter said:**
> Which apps only have gui-only tools, I haven't seen any

Two come to mind for me:

[LIST=1]
[*]Gnome Screensaver - There used to be an option in the GUI config to disable fading on screensaver activation.  However, in Dapper the GUI config has been *simplified* to remove this and other options.  If there were an intuitive config file, I could just manually go turn this off (it doesn't work with the Thinkpad T40); however, because the config file is obscured somewhere, I had to use the suggestion in one of these threads to trick xscreensaver into configuring fading for me.

[*]Gnome file associations - Adding an "Open With" association is easy enough by right-clicking a file, but has anyone ever wanted to remove one of those associations?  I have not found an intuitive way to do this.  Again, if the associations were in a simple config file, I could manually edit them myself.
[/LIST]

---

### Post by aysiu on 2006-10-18
The way Gnome does configuration makes it difficult. The only thing you'll see in your configuration files are the changes from the originals (not the originals themselves).

For example, when I look at my ~/.gconf/apps/gnome-screensaver/%gconf.xml file, all I see is ```
<?xml version="1.0"?>
<gconf>
        <entry name="mode" mtime="1160549170" type="string">
                <stringvalue>single</stringvalue>
        </entry>
        <entry name="themes" mtime="1160549170" type="list" ltype="string">
                <li type="string">
                        <stringvalue>screensavers-glslideshow</stringvalue>
                </li>
        </entry>
</gconf>
``` I tried to find the default config file, but I couldn't find one that makes any sense in /etc or /usr or /lib.

This is why I use IceWM.

---

### Post by Charles Hand on 2006-10-18
Try adding a launcher to a gnome panel through CLI.

And Beryl, the .settings files are text, but might just as well be binary for all the functionality they (don't) expose.

I'm just saying, openness is a key differentiator of Linux over the alternative OSes, and that openness seems to be creeping away. We ought to remind project architects of that fact from time to time.

---

### Post by aysiu on 2006-10-18
I'm just saying I don't think it's creeping away from Linux, just Gnome.

---

### Post by angkor on 2006-10-19
> **Charles Hand said:**
> Try adding a launcher to a gnome panel through CLI.

And Beryl, the .settings files are text, but might just as well be binary for all the functionality they (don't) expose.

I'm just saying, openness is a key differentiator of Linux over the alternative OSes, and that openness seems to be creeping away. We ought to remind project architects of that fact from time to time.

Beryl is very new alpha software so maybe this will improve in the future, I don't know. You can remind the beryl developers [here]("http://bugs.beryl-project.org/"). For your comments on Gnome's config files I agree.

---

### Post by graabein on 2006-10-19
I think both ways should be the goal. It should be easy to remotely configure a machine without having to run X, and at the same time have a GUI that presents the different options and prevents incorrect input.

Writing GUI's for config file editing shouldn't be that hard a job. Config files are often quite similar also so maybe this could be done with that in mind?

:-k

---

### Post by Shin_Gouki2501 on 2006-10-19
"Is Linux configuration destined to become just like Windows?"
No it has ro rise above, XML is nice for the machine, still i personally would not like to look fordependencies or paths in a text file...
the gui have to offer for me the necessary information!
wbr shin gouki

---

### Post by nocturn on 2006-10-19
> **Charles Hand said:**
> Thanks for the tip. Interesting window manager. Fast, too! It still uses the old clunky fonts, but I'll play with it.

I think KDE still has clean, text config files too, with a modern GUI and anti-aliased fonts.

---

### Post by nocturn on 2006-10-19
> **zenwhen said:**
> If you give me a tool to configure options on my OS and do not provide me a readable plain text way to deal with those settings, then you have not provided me anything but a layer between me and functionality.

What happens when your GUI tool breaks? What if I want to configure your application or setting remotely without super slow x forwarding?

I am out of luck. 

I am pointing the finger at application developers who do not provide access to well commented configuration files.

**YOU** are destroying one of Linux's main advantages. Please think about the GUI user and the user who can live without a preference pane for every setting. Think about the people who will not be able to properly use your tool if you hide every setting within a tab on an advanced settings menu.

100% agree!

---

### Post by Steveire on 2006-10-19
Nocturn, can you tell me what file to edit to change/view the current proxy configuration on the CLI? ie, the gui that shows when you type
```
 kcmshell proxy
```

---

### Post by Steveire on 2006-10-19
Bump. Anyone? I know I can export http_proxy=http://pr[noparse]oxy:por[/noparse]t for bash sessions, but I want to control konqueror/kontact etc.

---

### Post by Shin_Gouki2501 on 2006-10-20
What happens when your GUI tool breaks? <-
I 100% disagree!
All gui tools available today suffer from misconcepts of ancient softwaredesigns , it is possible to build a robust gui. Which works ALWAYS even if the Programm logic itselves creates Errors.
The main Problem is that most GUI Programms simply close when an Error occurs and their Error Output is... LOW to none.
It is not a bad thing when a programm or the Progamm logic crashes, BUT it is necessary that htere is an correct Error Output which informs the user. -> Like with the CLI
the GUI is just another IO Mapping concept which is badly implemented in "GUI"-Frameworks today.
Its sad that this very much needed direction is ABSOLUTLY ignored by OS software devs.. :(
But windows is not any better ..
as i said Linux/OS need to rise above.
It is necessary to address and fix the wide know issues of "GUI"-related Programms.

And please dont misunderstand me, in my opinion the CLI is also very usefull in/with Linux. BUT u have to enable the User to choose :
How can i do "something" in Linux:
*by CLI
*by GUI

thats my point of view
wbr Shin Gouki

---

### Post by argie on 2006-10-20
I prefer if the text configuration mode is still available. 

"Oh your config doesn't work? Paste this in and see if it does."
vs.
"Oh, your config doesn't work? Go to TabX and Click on ButtonY, then to TabZ and Click ButtonA, dialog1 should popup, click advanced..., enter 2048 in the Kbytes text box and close everything"

Naturally, that's an extreme case

---

### Post by Shin_Gouki2501 on 2006-10-20
right most GUI Programms suffer from the miss concepts:
u are refering to :
[http://linux.oneandoneis2.org/LNW1.htm](http://linux.oneandoneis2.org/LNW1.htm)
easy-direct route
if a gui is designed the "right" way u Could actually use the direct way.
wbr Shin Gouki

---

### Post by mssever on 2006-10-20
I agree with the OP. GUI configuration is nice--very important, even--but there's no reason that those configuration settings can't be stored in human-accessable format. Granted, most are still plain text, but I haven't yet figured out how to change gconf settings without using gconf-editor. The point is that ideally every configuration option should be GUI-accessible, while preserve the usability that comes from being able to hand-edit files.

Furthermore, for those of us who know what we're doing, manually editing configuration files is a whole lot easier in many cases than using a GUI. Compare Apache with IIS. IIS is more newbie-friendly, but once I learned my way around Apache, I find Apache configuration to be much easier.

---

### Post by Shin_Gouki2501 on 2006-10-20
right if u get stuck with IIS, it can be quite annoying, :O

---

### Post by airtonix on 2007-07-03
I believe conf files require an ISO standrad....it needs to be taken seriously as the lightest, fastest, and easiest way to save and trasnport configurations...
(well apart from JSON)

SO....all of you who love the gui and think there isnt a problem with missing or config files using non-standrad formats....

1. open gnome proxy settings. point it at a proxy server on YOUR INTERNAL NETWORK.

2.now remove the DesktopEnviroment. im dumping you to the term forever baby.
  > sudo apt-get remove nautlius gnome-panel gnome-applets banshee rhythmbox gnome*

3 then ctrl+alt+f1 then login

4. type :>  sudo /etc/init.d/gdm stop (using sudo password)

Kay now you geniuses.....try to change your network proxy. remember no apt-get'n the GUI back.

ps: (all those web-developers out there wouldnt be where they are if webpages didnt use standardised syntax and formating methods. )

---

### Post by brim4brim on 2007-07-03
> **mssever said:**
> I agree with the OP. GUI configuration is nice--very important, even--but there's no reason that those configuration settings can't be stored in human-accessable format. Granted, most are still plain text, but I haven't yet figured out how to change gconf settings without using gconf-editor. The point is that ideally every configuration option should be GUI-accessible, while preserve the usability that comes from being able to hand-edit files.

Furthermore, for those of us who know what we're doing, manually editing configuration files is a whole lot easier in many cases than using a GUI. Compare Apache with IIS. IIS is more newbie-friendly, but once I learned my way around Apache, I find Apache configuration to be much easier.

Well Gconf exists I think because Gnome configuration would be such a pain by just using a text file because it is so big.

All Gconf does is change settings in a text file for you anyway so its not like its a million miles away from a text editor itself.

I agree that it should be possible to edit configurations by hand but it isn't always the most practical way.  In the case of Gconf, maybe they are just saving you from yourself!

---

### Post by ssam on 2007-07-03
gconf can be configured on the command line.

man gconftool

when you use the gconf tools to edit gconf settings the new values get transmitted to program, so changes can take effect instantly. also the tools can prevent you making syntax errors in the conf files. gconf knows about default and legal values, so if you break anything then you can reset each key to its default.

the backend does not need to store the information in xml. you could make a plugin to store it however you wanted.

have a read of [http://www.gnome.org/projects/gconf/index.html](http://www.gnome.org/projects/gconf/index.html)

---

### Post by Tundro Walker on 2007-07-03
I personally can't stand the trend of using XML for config files.  I can understand it, but I can't stand it.  I guess the idea is to make editing the "txt" file (XML in this case) such a pain in the butt that folks are forced to use a GUI.  (I'm kidding, of course, but sometimes it feels that way.)

---

### Post by ssam on 2007-07-03
> **Tundro Walker said:**
> I personally can't stand the trend of using XML for config files.  I can understand it, but I can't stand it.  I guess the idea is to make editing the "txt" file (XML in this case) such a pain in the butt that folks are forced to use a GUI.  (I'm kidding, of course, but sometimes it feels that way.)

<sarcasm>
ascii txt is really hard to edit, if you just miss out one 0 or 1, then you byte can get out of line, and the whole file is unreadable. you have to be really good at adding in binary to understand it all.
</sarcasm>

with out a good text editor plain text is hard to edit. with one it becomes impossible to make an invalid text file.

with out a good xml editor xml is hard to edit. a search from linux xml editor on google gives a lot of results

---

### Post by brim4brim on 2007-07-03
XML files are fine, its the lack of comments that is the real pain I think in most code.

---

### Post by ssam on 2007-07-03
> **brim4brim said:**
> XML files are fine, its the lack of comments that is the real pain I think in most code.

for gconf the description of what each setting does and which values are valid are in the schema. for example the nautilus schema is at

/usr/share/gconf/schemas/apps_nautilus_preferences.schemas

---

### Post by jrusso2 on 2007-07-03
> **Charles Hand said:**
> I misrepresented myself. I'm not AGAINST gui configuration. I'm just saying that a strength of Linux has always been that the gui configurators work on text files. Thus, there is always a basic, consistent level at which you can configure things that the gui doesn't let you do, or automate configuration using scripts. It's all part of having control under the hood when you want to, which is a primary difference between Linux and Windows.

Another reason Gnome is bad,  Stay away from Gnome as they are the ones that have strayed from using Text files.

---

### Post by @trophy on 2007-07-03
I agree with the OP... nothing wrong with GUIs, but have them operate on the same old text files that have been used to configure everything since Dinosaurs roamed the earth.  And LEAVE THE COMMENTS IN THE FILES!!!

---

### Post by mssever on 2007-07-04
> **airtonix said:**
> *<snip>*
Kay now you geniuses.....try to change your network proxy. remember no apt-get'n the GUI back.
Use ```
 gconftool --all-entries /system/proxy; gconftool --all-entries http_proxy
``` to list the available proxy settings. Type ```
gconftool --set --type=*type* /path/to/key "new value"
``` to change a setting and have it instantly applied.

This really should be better documented. I only discovered it last week after a year of using a Gnome system that is sufficiently modern to use gconf. Now, if you've really removed all the Gnome stuff (why would you do such a thing in real life and still care about Gnome settings?), it's possible, though difficult, to locate the appropriate text file and edit it by hand.

> **brim4brim said:**
> Well Gconf exists I think because Gnome configuration would be such a pain by just using a text file because it is so big.

*<snip>*

I agree that it should be possible to edit configurations by hand but it isn't always the most practical way.  In the case of Gconf, maybe they are just saving you from yourself!
Gconf does provide a convenient way to manage settings, but I hope they aren't trying to save me from myself. If I break my system, that's my fault.

The thing that makes Gnome config files difficult to edit by hand isn't their size (nobody would store all of Gnome's settings in a single file) but their format. XML files aren't easy to manually edit, compared to plain text files (think Apache config). But, XML was designed more as a machine-readable format than as a human-readable format.

> **jrusso2 said:**
> Another reason Gnome is bad,  Stay away from Gnome as they are the ones that have strayed from using Text files.
No, Gnome still uses text files; they just try to hide them. But I haven't found an alternative to Gnome that I like.

---

### Post by Shin_Gouki2501 on 2007-07-04
I think its my 3rd month with xubuntu and i have isntaleld somethings were ( of course?!) 
I had to configure something via text file...
For most cases it works somehow OK
But  i think its important to have a GUI to give the user a bit more overview of WHAt the programm can actually do.
My example:
i installes FTP server , and i did config my stuff but the FTP still didn't seem to apply my changes, so what "obviously " i had to restart the server to affect changes BUT if u never isntalled an FTP server Before u might not know.
A GUI could sugegst: to apply ur changes made to the configuration u have to restart ur FTP server, do you want to restart now?

Such "human"logic things need to be implemented into A LOT of linux programms. 
Most People tend to say: learn the logic of the programm but i think thats the worng apporach.

wbr Shin Gouki

---

### Post by mssever on 2007-07-05
I don't think that anyone's arguing against GUI configuration. Ideally, every GUI program should be fully configurable via both methods.

When it comes to servers, though, the situation's a bit different. Servers are intended for more professional type use. So they should be designed with that kind of user in mind. If you try to run a server without reading the documentation, you should expect problems. Servers are designed to let administrators do what they need to do without undue restrictions, and because of that, you can find yourself in deep water if you don't know what you're doing. In addition, writing a GUI for a server is a bit silly. Most servers are installed on a remote machine, and the remote machine is administered via the command line. A GUI would run slowly over the network (with X forwarding) and only would benefit a few newbies.

When I installed my first webserver (for PHP development, not production), I tried both Apache and Microsoft IIS. IIS was much easier for me to get started, because its configuration is entirely GUI-based. But since I've buckled down and read the relevant portions of the Apache manual, I'd never go back to IIS. Apache's text files are much easier to use.

The upshot of this is that if you install an FTP server--or any other kind of server--remember that it's written for professionals, not average desktop users.

---

### Post by Atomic Dog on 2007-07-05
> **Demio said:**
> Do you guys even read his posts?

He's complaining about the obscurity in some config files (eg.: the ones in GNOME and Beryl). 

They are editable by text but not either nicely commented or very readable.

He's right about that.

---

### Post by airtonix on 2007-07-09
I dont have a problem with xml....its more standardised than most conf files formats.....much more so..

One of the cool thing i like about html and thus more so with xml is the logical relationship of nodes.

[HTML]<book>
 <page>
  <paragraph/>
  <paragraph/>
  <paragraph/>
 </page>
 <page>
  <paragraph/>
  <paragraph/>
  <paragraph/>
 </page>
 <page>
  <paragraph/>
  <paragraph/>
  <paragraph/>
 </page>
</book>[/HTML]

anyone who has been using xml would also know the diff between the two schema languages.....one i cant rememeber(the new one) the other is DTD.

one uses non-xml syntax to define xml schema (stupid as it steps outside of language boundries) 
the other uses xml to define the schema. (smarter)

even better xml works with XSLT which can make an unreadable XML conf file into a useable form GUI.

with only a XML and aXSLT file you can make a gui. 

question: can the gtk lib make a GUI form resulting from a transformation of a XML file with a XSLT file?

I've actually been working with xml since 199?(so long)....I learnt it from the MSDN subscription a friend had.

So me personally, i have approached text-configs with a objectification in mind....xml and its "fragments" or "leaves" belonging to a "branch" that are attached to a "trunk" which makes a "tree".

On first glance I also notice the compiz configurator seems to be the only way to config compiz....im most proly wrong thou

2nd question: does gconf have settings in file? is file one large one? or many small ones sorted in logicall-named folders? can i load one individually in gconf?

---

### Post by mrgnash on 2007-07-09
> **Charles Hand said:**
> I misrepresented myself. I'm not AGAINST gui configuration. I'm just saying that a strength of Linux has always been that the gui configurators work on text files. Thus, there is always a basic, consistent level at which you can configure things that the gui doesn't let you do, or automate configuration using scripts. It's all part of having control under the hood when you want to, which is a primary difference between Linux and Windows.

Pretty much my line of thinking as well. I think it is important to allow for the sort of accessibility that the GUI interface provides, and that most things should be able to be driven from there. However, I think it's equally important that below that, there is a consistent, and human readable, layer of configuration settings accessible to the more advanced/CLI savvy users. I can't really see why both worlds can't mutually coexist, and am a little worried by the current trend as well.

---

### Post by cobrn1 on 2007-07-09
I like being able to modify using both the CLI and a GUI. Having human-readable config files was a breath of fresh air when moving from windows, and it's essential for servers. However, it's normally much easier to use a GUI and that's why I like having both options. 90% of the time I'd use the GUI, but having the CLI option is just too valuable to dispense with, and I'd never, ever suggest that. Infact, it would upset me greatly...

---

