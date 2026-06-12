---
title: "Powershell and Bash"
date: 2009-11-02
forum: The Cafe
---

### Post by hoppipolla on 2009-11-02
I keep hearing about this "Powershell" thing in 7/Vista and am wondering how it compares to Bash? I haven't used it yet but I'll install it when I get on 7... or does it come pre-installed? o.O


A confused Hoppi :)

---

### Post by NoaHall on 2009-11-02
You can get it in XP(since SP3, I think). It's more powerful than bash, but not as useful the terminal.

---

### Post by koenn on 2009-11-02
It's an installable program, I don't think it's included by default.
It's been around for a while - since 2005 or so I think.

I havent' used it, but from what I see, it doesn't compare to bash. 
It has an object-based syntax that lets you call  methods from just about every windows component - not your typical shell where you call commands or programs, but essentially something that makes sense for Windows but not necessarily anywhere else.

---

### Post by MicrosoftFan on 2009-11-02
It was available before but is now installed (version 2) by default in Windows 7 and Windows Server 2008 R2; these are the first OS's to do so.
 
Yes of course you can call external programs with it, but it's main focus is cmdlets. Secondarily you can use all of the .Net Framework and WMI with it, meaning there's really nothing in Windows you can't do with PowerShell. 
 
Here's a very good introduction video by Jeffrey Snover, one of PS's creators:
[http://blog.jaoo.dk/2009/02/09/windows-powershell-a-command-line-shell-and-scripting-language/](http://blog.jaoo.dk/2009/02/09/windows-powershell-a-command-line-shell-and-scripting-language/)

---

### Post by koenn on 2009-11-02
> **MicrosoftFan said:**
> 
Yes of course you can call external programs with it, but it's main focus is cmdlets. Secondarily you can use all of the .Net Framework and WMI with it, meaning there's really nothing in Windows you can't do with PowerShell. 
That's what I meant - that you'd rather call a WMI method than execute an external program, not that it would be impossible to call an external program. 

And therefore it doesn't compare to bash - it's a solution to make a GUI system scriptable, to let you programmatically manage an operating system that was originally designed to be managed through a GUI. Bash is the exact opposite : a programmable shell to a text-oriented system.

---

### Post by ukripper on 2009-11-02
Bash is much more powerful, only if you know what you doing and also if you are good at shell scripting. 

You can even tune the Linux kernel using bash. Whereas Microsoft won't allow you to hack the kernel.

Powershell is by far high-level tool can't be compared with almighty Bash.

---

### Post by hoppipolla on 2009-11-02
> **MicrosoftFan said:**
> It was available before but is now installed (version 2) by default in Windows 7 and Windows Server 2008 R2; these are the first OS's to do so.
 
Yes of course you can call external programs with it, but it's main focus is cmdlets. Secondarily you can use all of the .Net Framework and WMI with it, meaning there's really nothing in Windows you can't do with PowerShell. 
 
Here's a very good introduction video by Jeffrey Snover, one of PS's creators:
[http://blog.jaoo.dk/2009/02/09/windows-powershell-a-command-line-shell-and-scripting-language/](http://blog.jaoo.dk/2009/02/09/windows-powershell-a-command-line-shell-and-scripting-language/)

yes but is it actually better as a terminal for day-to-day use? I mean in BASH I can do pretty much everything I can do in a GUI and often more.

---

### Post by Penguin Guy on 2009-11-02
Not bad, the idea of an object-oriented shell seems funny though. From the screenshot it looks like they've have added a sudo command as well.

---

### Post by NoaHall on 2009-11-02
It's more powerful for servers. You can't say that bash is better than it. Our terminal powers are better though.

---

### Post by koenn on 2009-11-02
> **NoaHall said:**
>  Our terminal powers are better though.
how's that ? Isn't bash what you run in your terminal ?

---

### Post by NoaHall on 2009-11-02
> **koenn said:**
> how's that ? Isn't bash what you run in your terminal ?

Yes, but powershell isn't great a launching applications. I mean, you wouldn't really do much scripting in the bash terminal - you'd write scripts to be used by bash.

---

### Post by koenn on 2009-11-02
> **Penguin Guy said:**
> Not bad, the idea of an object-oriented shell seems funny though. It's a sensible approach for managing the complexity of Windows - got to give them credit for that. 


> **Penguin Guy said:**
> From the screenshot it looks like they've have added a sudo command as well.
Yeah, they learned a lot from unix / linux.
The entire concept of a programmable shell as a unified means to manage the entire system is something they'd given up since the started NT.

---

### Post by MicrosoftFan on 2009-11-02
> **hoppipolla said:**
> yes but is it actually better as a terminal for day-to-day use? I mean in BASH I can do pretty much everything I can do in a GUI and often more.
 
I don't really know what 'day to day CLI use' for a home Windows user would be (maybe if you could give some examples). For server admin you can basically do anything with files, processes, the registry, installed MS software etc, as well as there being cmdets to deal with Active Directory, Exchange, SQL Server etc. Though it's still fairly early days for PS and more products by MS and other companies are adding support for PS all the time.
 
However the video gives a good starter on how the shell enviroment is an evolution of Bash & others.
 
> **ukripper said:**
>  
You can even tune the Linux kernel using bash. Whereas Microsoft won't allow you to hack the kernel.
 
Linux allows you to 'tune the kernel' and Windows doesn't. I don't see what that has to do with Bash vs PowerShell.
 
> **NoaHall said:**
> Yes, but powershell isn't great a launching applications. 
 
What do you mean by that?

---

### Post by MicrosoftFan on 2009-11-02
> **koenn said:**
> That's what I meant - that you'd rather call a WMI method than execute an external program, not that it would be impossible to call an external program. 
 
Yes, although PowerShell is designed foremost to be used by admins and not by programmers, and so cmdlets are the primary method of doing things, rather than some object-oriented approach. WMI is just there as a fallback for the parts where no-one has written a suitable cmdlet yet.

---

### Post by ukripper on 2009-11-02
> **MicrosoftFan said:**
> 
 

 
Linux allows you to 'tune the kernel' and Windows doesn't. I don't see what that has to do with Bash vs PowerShell.
 

 


That shows one very important thing what Bash can do in Linux and Powershell can't in windows. It is related if you see it in broader picture not narrowly dismissing the fact.

---

### Post by NoaHall on 2009-11-02
> **MicrosoftFan said:**
> 
What do you mean by that?

I mean Powershell just isn't great at loading external apps like Bash is. Powershell's built in features are great though, especially for Microsoft servers.

---

### Post by koenn on 2009-11-02
> **ukripper said:**
> That shows one very important thing what Bash can do in Linux and Powershell can't in windows. It is related if you see it in broader picture not narrowly dismissing the fact.

your example is a feature of Linux vs. a feature of Windows, not a feature of bash vs. a feature of PowerShell.

Meaning: it may be true, but it has no relevance here.

---

### Post by lykwydchykyn on 2009-11-02
> **Penguin Guy said:**
> Not bad, the idea of an object-oriented shell seems funny though. From the screenshot it looks like they've have added a sudo command as well.

Reminds me of dbus calls in a way.  Interesting stuff.

---

### Post by ukripper on 2009-11-02
> **koenn said:**
> your example is a feature of Linux vs. a feature of Windows, not a feature of bash vs. a feature of PowerShell.

Meaning: it may be true, but it has no relevance here.

In that case this whole thread renders irrelevant. There is no direct comparison of Bash and powershell.

---

### Post by Xbehave on 2009-11-02
> **NoaHall said:**
> Yes, but powershell isn't great a launching applications. I mean, you wouldn't really do much scripting in the bash terminal - you'd write scripts to be used by bash.
You may not but, simple scripts is where bash (+gnu utils) really shines, for example
cp /path/to/file{,~}
su -c 'ionice -c 1 -p $(pgrep ^mplayer$) ; renice -5 $(pgrep ^mplayer$)'
PID=$(pgrep ktorrent); ionice -c 3 -p "$PID"; renice +20 "$PID"

and while there is a point where you give up and write a script, you can end up with a solution like
> cat /usr/share/dict/words | fgrep -v "'" | perl -ne 'chomp($_); @b=split(//,$_); print join("", sort(@b))." ".$_."\n";' | tee lookup.txt | perl -pe 's/^([^ ]+) .*/\1/g' | awk '{ print length, $0 }' | sort -n | awk '{$1=""; print $0}' | uniq -c | sort -nr | egrep "^[^0-9]+2 " | awk '{ print length, $0 }' | sort -n | awk '{$1=""; print $0}' | perl -pe 's/[ 0-9]//g' | xargs -i grep {} lookup.txt | perl -pe 's/[^ ]+ //g' | tail -n2

sure you can do that under other shells, but a posix shell + gnu utils >> powershell as an everyday shell AND as a programming solution (while i personally prefer python for scripting, bash is a very powerful language)

---

### Post by koenn on 2009-11-02
> **ukripper said:**
>  There is no direct comparison of Bash and powershell.
see post #3

---

### Post by koenn on 2009-11-02
> **Xbehave said:**
>  ...
sure you can do that under other shells, but a posix shell + gnu utils >> powershell as an everyday shell AND as a programming solution (while i personally prefer python for scripting, bash is a very powerful language)
and all of that works because linux is a text-oriented system. Most of that simply won't work in a GUI-oriented system, especially if that system also does not use flat text files to store configuration.

---

### Post by hessiess on 2009-11-02
How does power shell compare to the regular windows terminal for running CLI applications? can it actually run programs by there name instead of requireing the full path to the program to be entered.

---

### Post by Xbehave on 2009-11-02
> and all of that works because linux **has** a text-oriented system. 
^edited, You can use linux using just a GUI
> Most of that simply won't work in a GUI-oriented system, especially if that system also does not use flat text files to store configuration.
You can manage kde (flat-text files) and gnome (registry, with registry editor), from the cli because the tools are there. There is nothing about GUIs that prevents CLI tools working, however the lack of flat text files does make it harder (gnome works around thing by providing tools)

---

### Post by NoaHall on 2009-11-02
Gnome does NOT have a registry.

---

### Post by Xbehave on 2009-11-02
> **NoaHall said:**
> Gnome does NOT have a registry.
What's gconf?
An api to give programs access to settings
What's a system registry?
An api to give programs access to settings

The only differences between gconf and windows resistry are
1) gconf only handles gnome settings
2) gconf has a multitude of backends
3) gconf gets corrupted less often (if ever)

additionally for most of the backends there are non-gconf tools that can be used to read/edit settings, but fundamentally gnome has a registry

---

### Post by jrothwell97 on 2009-11-02
> **hessiess said:**
> How does power shell compare to the regular windows terminal for running CLI applications? can it actually run programs by there name instead of requireing the full path to the program to be entered.

PowerShell kicks cmd.exe to the kerb and jumps on it until it's had enough.

---

### Post by Xbehave on 2009-11-02
> **jrothwell97 said:**
> PowerShell kicks cmd.exe to the kerb and jumps on it until it's had enough.
To be fair the linux kernel's inbuilt shell does that, does powershell allow you to launch binaries without moving to the correct directory first?

---

### Post by jrothwell97 on 2009-11-02
> **Xbehave said:**
> To be fair the linux kernel's inbuilt shell does that, does powershell allow you to launch binaries without moving to the correct directory first?

Yes, as did cmd.exe.

As long as it's in a path Windows can expect it to be in: I've not done extensive testing, but it probably looks in \Program Files as well as \Windows.

Of course, if it's stored at F:\obscure\folder\Music\miscategorised stuff\bin\App.exe, it won't find it, because it doesn't index the entire system and it leads to potential conflicts (what if there are two App.exes?)

Of course, you can also enter the relative or absolute path:
```
> ..\Binaries\App.exe
```
which is remarkably similar to
```
$ ../Binaries/app
```
In short... it's a shell.

(Also, the Linux command shell, bash, dash, tcsh, whatever, is *not* a part of the kernel - it's just almost always bundled with it to make a usable distribution. :))

---

### Post by koenn on 2009-11-02
> **Xbehave said:**
> ^edited, You can use linux using just a GUI

You can manage kde (flat-text files) and gnome (registry, with registry editor), from the cli because the tools are there. There is nothing about GUIs that prevents CLI tools working, however the lack of flat text files does make it harder (gnome works around thing by providing tools)

Nope, Linux **is** a text oriented system. The entire system is build on the premise that everything is a file - preferably an ASCII text file.  All configuration is text - mostly plain text, sometimes structured in xml. Interfaces between programs are text streams. Input and output are text streams. And so on.

Yes, you can run GUI programs, window managers and desktop environments on Linux, but they're just programs. That doesn't change the text-oriented paradigm of the OS they run on. 

Windows is entirely different. The GUI is an integral part of the the OS. Configuration is in a numver of binary datastores which can only be handled by dedicated programs that have intimate knowledge of the internal structure of that datastore. Each datastore will have its own set of management tools. Most of these tools can only be managed through GUIs, although some expose a scriptable API, which then often has an entirely different syntax and semantics compared to the GUI, and may expose more, less, or different functionality than the GUI. 

It's that sort of problem  that powershell aims to fix (and it looks like the PS guys did a good job).

---

### Post by MicrosoftFan on 2009-11-02
> **Xbehave said:**
> To be fair the linux kernel's inbuilt shell does that, does powershell allow you to launch binaries without moving to the correct directory first?
 
As with cmd.exe you only need to type the name for programs that exist in a folder on your path or where a link to the file exists in a folder on your path. This is the same as Bash, no?
 
Additionally with PS over CMD you can create aliases for files in other directories. eg:
```
PS> Set-Alias ex 'C:\Program Files\Example\exampleprog.exe'
```
 
> **Xbehave said:**
> 
cat /usr/share/dict/words | fgrep -v "'" | perl -ne 'chomp($_); @b=split(//,$_); print join("", sort(@b))." ".$_."\n";' | tee lookup.txt | perl -pe 's/^([^ ]+) .*/\1/g' | awk '{ print length, $0 }' | sort -n | awk '{$1=""; print $0}' | uniq -c | sort -nr | egrep "^[^0-9]+2 " | awk '{ print length, $0 }' | sort -n | awk '{$1=""; print $0}' | perl -pe 's/[ 0-9]//g' | xargs -i grep {} lookup.txt | perl -pe 's/[^ ]+ //g' | tail -n2 

 
What is this script meant to do and is this what you would normally write for that task?

---

### Post by Xbehave on 2009-11-02
> **jrothwell97 said:**
> (Also, the Linux command shell, bash, dash, tcsh, whatever, is *not* a part of the kernel - it's just almost always bundled with it to make a usable distribution. :))
you are right i was confusing the ash shell that is built into init with a shell that's built into the kernel

> As with cmd.exe you only need to type the name for programs that exist in a folder on your path or where a link to the file exists in a folder on your path. This is the same as Bash, no?
No under a posix shell you can run any binary that is in your PATH setting (usually something like /usr/local/bin:/usr/bin:/bin:/usr/games:/usr/local/sbin:/usr/sbin:/sbin:/opt/bin) or your current directory, e.g you can run firefox without being in /usr/share/lib/firefox or c:\programs\mozilla\firefox\

> What is this script meant to do and is this what you would normally write for that task? I have no idea it's just an example, i took from the xkcd blag because there is nothing interesting in my current history. I would guess he is looking for words of a particular form, so it would be best suited by a perl script, however i would also suggest that it was put together bit by bit as the users needs changed (a give away is the tee command that puts stuff into a file only to use the file with xargs later)

> Nope, Linux is a text oriented system. The entire system is build on the premise that everything is a file 
Actually that's plan9, linux is an amalgamation of many design principles. Most of your lower tools are configured by text files (and the relevant GUI tools to edit them), but gnome does all its configuration through gconf, which can store data in any format that the backends provide (I heard there were LDAP and SQL backends as well as the standard XML).

> That doesn't change the text-oriented paradigm of the OS they run on. 
If you run gnome/kde, you will mostly interact with gnome/kde, it doesn't really matter how the underlying systems are configured (especially if you configure them using a GUI)

---

### Post by koenn on 2009-11-02
> **Xbehave said:**
> 
Actually that's plan9, linux is an amalgamation of many design principles. Most of your lower tools are configured by text files (and the relevant GUI tools to edit them), but gnome does all its configuration through gconf, which ... 

If you run gnome/kde, you will mostly interact with gnome/kde, it doesn't really matter how the underlying systems are configured (especially if you configure them using a GUI)

The everything is a file thing comes from unix, actually. Plan 9 is just reusing it, as is linux. 

And it doesn't really matter what gnome or kde does. These are not operating systems. Powershell is about having commandline access to an *OS* that is designed to process events rather that text.

Although with a bit of a stretch, you could say that gconf is to gnome what powershell is to Windows, with that difference that Windows is an operating system, and gnome is a userland application. 

The difference becomes clear when you compare  a bash pipe line with a powershell pipeline : they look pretty similar on your screen, but the bash pipe passes text from one program to another, a powershell passes objects (and has a complex processing infrastructure underneath it to make this work, while a bash pipe is a straight connection between one program's stdout and the next program's stdin).

---

### Post by MicrosoftFan on 2009-11-02
> **Xbehave said:**
> No under a posix shell you can run any binary that is in your PATH setting (usually something like /usr/local/bin:/usr/bin:/bin:/usr/games:/usr/local/sbin:/usr/sbin:/sbin:/opt/bin) or your current directory, e.g you can run firefox without being in /usr/share/lib/firefox or c:\programs\mozilla\firefox\
 
Isn't that what I said? How is that different from Windows? Of course, the organization of files in Windows is different, you don't have all the executables in just a few folders, but the way the command line shell handles short file names is the same.
 
> **Xbehave said:**
>  
I have no idea it's just an example, i took from the xkcd blag because there is nothing interesting in my current history. I would guess he is looking for words of a particular form, so it would be best suited by a perl script, however i would also suggest that it was put together bit by bit as the users needs changed (a give away is the tee command that puts stuff into a file only to use the file with xargs later)
 
 
Shame since I thought it would have been good to illustrate how it would be done in PowerShell. It seems to create a file with the words and with their letters sorted in alphabetical order, though it seemed a long script for just that & I didn't understand all of it.

---

### Post by Xbehave on 2009-11-02
> **MicrosoftFan said:**
> Isn't that what I said? How is that different from Windows? Of course, the organization of files in Windows is different, you don't have all the executables in just a few folders, but the way the command line shell handles short file names is the same.
Sorry re reading it i didn't make myself clear. 
In a POSIX shell there is a $PATH variable, this is not the same as your current working dirrectory (which is given by $PWD), the $PATH variable is a list of places to execute programs from. Is this the same under widows?

---

### Post by Mr. Picklesworth on 2009-11-02
For those suffering from Powershell envy (since it is a pretty elegant design), check out [Hotwire]("http://code.google.com/p/hotwire-shell/") (happily available from Ubuntu's Software Centre, with [more info here]("http://cdn.hotwire-shell.org/index.html")).

---

### Post by hoppipolla on 2009-11-02
It does seem that BASH is still better for users like me who just dip in and out of the prompt to execute a quick command, or who sometimes do some brief system maintenance and random tinkering. I don't really do scripts or anything like that so I just want a terminal that's powerful, comprehensive and easy to use :)

Correct me if I'm wrong here :)

---

### Post by MicrosoftFan on 2009-11-03
> **Xbehave said:**
> Is this the same under windows?
 
Yes, sorry this is what I meant by "a folder on your path". Windows also has the PATH variable, for example mine is "C:\Windows\system32; C:\Windows; C:\Windows\System32\Wbem; C:\Windows\System32\WindowsPowerShell\v1.0\; C:\Users\Me\Programs". It's accessible as %PATH% in Cmd.exe or $env:Path in PowerShell. And in the same way Windows searches these directories as well as the current after you type in a command.

---

### Post by MicrosoftFan on 2009-11-03
> **hoppipolla said:**
> a terminal that's powerful, comprehensive and easy to use
Sounds exactly like PowerShell :D
But I don't know what "brief system maintenance and random tinkering" a home Windows user would do.

---

### Post by praveesh on 2009-11-03
Interesting . Windows is improving ?

---

### Post by Xbehave on 2009-11-03
> **MicrosoftFan said:**
> Sounds exactly like PowerShell :D
But I don't know what "brief system maintenance and random tinkering" a home Windows user would do.
backup files?
clean clutter? (ironically most windows users install a separate app for that)
customise their system?
doing fairly simple repetitive tasks, quickly? (e.g renaming all files of the form DSCYYYYDDMM.jpeg to photo-dd-MM-YY.jpeg), again there is probably an app for that but if you are familiar with regex it's probably quicker to do in a few commands))

Obviously you can ignore the CLI if you want to but it is a very powerful tool for a lot of stuff (then again so is powershell apparently)

---

### Post by hoppipolla on 2009-11-03
> **MicrosoftFan said:**
> Sounds exactly like PowerShell :D
But I don't know what "brief system maintenance and random tinkering" a home Windows user would do.

Well, I use BASH for quickly installing and removing software, updating my system, doing quick operations as root, firing up applications for the GUI with specific parameters, changing runlevel, monitoring program activity/system load, file managing, tech support of other people's systems (such as adding PPAs they might need etc), zip and unzip files etc etc. BASH is also incredibly detailed and allows me to throw together almost any command I like. I can recover my system with BASH if the GUI goes wrong too, as I always have a terminal to fall back on.

---

### Post by Xbehave on 2009-11-03
> **hoppipolla said:**
> Well, I use BASH for quickly installing and removing software, updating my system, doing quick operations as root, firing up applications for the GUI with specific parameters, changing runlevel, monitoring program activity/system load, file managing, tech support of other people's systems (such as adding PPAs they might need etc), zip and unzip files etc etc. BASH is also incredibly detailed and allows me to throw together almost any command I like. I can recover my system with BASH if the GUI goes wrong too, as I always have a terminal to fall back on.
TBF how much of that would a windows user do? I belive that was MSfan's point

---

### Post by hoppipolla on 2009-11-03
> **Xbehave said:**
> TBF how much of that would a windows user do? I belive that was MSfan's point
True, but then how many scripts does your average user write? xD

I guess I just feel that for your average desktop user needing tech support or with a light technical edge like me, having BASH hanging around seems to still be better than having Powershell.

---

### Post by MicrosoftFan on 2009-11-03
> **Xbehave said:**
> backup files?
clean clutter? (ironically most windows users install a separate app for that)
customise their system?

 
For backup, yes the windows or a 3rd party backup program can be run from the command line, though I don't know the specifics. Or if just creating copies of the files cmd.exe might work just as well as powershell here.
 
For cleaning, the windows disk cleanup (cleanmgr.exe) can be run from the start menu, cmd.exe or powershell. If you have an extra 3rd-party app it may or may not offer command line options.
 
Customise their system: Still don't really understand what this means in a windows context and why you'd want the CLI to do it.
 
> **Xbehave said:**
> 
doing fairly simple repetitive tasks, quickly?
Yes this is what the CLI is good for. PowerShell has the -match and -replace operators for working with Regexes. Taking that example (DSCYYYYDDMM.jpeg -> photo-dd-MM-YY.jpeg) I can use the Rename-Item cmdlet with the regex replacement in a lambda:
```

#Full Version
Get-ChildItem * | Rename-Item -NewName { $_ -replace '.+\d\d(\d\d)(\d\d)(\d\d)', 'photo-$2-$3-$1' }
 
#Short Version
ls | ren -n { $_ -replace '.+\d\d(\d\d)(\d\d)(\d\d)', 'photo-$2-$3-$1' }

```
 
Of course if i was going to be renaming many files with regexes a lot I'd write a function to cut down on the typing some more.
 
> **hoppipolla said:**
> Well, I use BASH for quickly installing and removing software, updating my system, doing quick operations as root, firing up applications for the GUI with specific parameters, changing runlevel, monitoring program activity/system load, file managing, tech support of other people's systems (such as adding PPAs they might need etc), zip and unzip files etc etc. BASH is also incredibly detailed and allows me to throw together almost any command I like. I can recover my system with BASH if the GUI goes wrong too, as I always have a terminal to fall back on.
 
> **hoppipolla said:**
> True, but then how many scripts does your average user write? xD
 
I guess I just feel that for your average desktop user needing tech support or with a light technical edge like me, having BASH hanging around seems to still be better than having Powershell.
 
You still seem to be thinking in Linux terms so Bash on Windows may be better for you, though many of those things (the ones that are appropriate to windows) only require single commands so cmd.exe would work just as well as powershell. 
 
Though for server admins PowerShell does help a lot for working with the system, and software and running processes on it. For example the Get-Process cmdlet gives you an object for each of the processes running on the system, which can be filtered, sorted or manipulated however you wish.

---

