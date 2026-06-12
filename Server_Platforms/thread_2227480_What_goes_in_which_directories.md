---
title: "What goes in which directories?"
date: 2014-06-02
forum: Server Platforms
---

### Post by sim085 on 2014-06-02
Hello,

I am reading about the various directories in root (/bin, /mnt, /usr, etc) and what they are meant to be used for. However I now have some questions.

I entered the command *which apache2* and the output was */usr/sbin/apache2*.
The description for /usr/sbin is *Non-essential system binaries, e.g., daemons for various network-services.*.
The description for /opt is *Optional application software packages*.

So why is apache2 installed in */usr/sbin* rather than */opt/<provider>/apache2*? 

Also, the description for /srv is *Site-specific data which are served by the system*.
So why does apache2 put websites in /var/www?
The description for /var is *Variable files*.
Why this is not */srv/www*?

---

### Post by tgalati4 on 2014-06-02
Directory assignments in linux are suggestions.  You can install any package anywhere.  As long as you have the correct permissions and the correct $PATH statement your programs will run.

> tgalati4@Mint14-Extensa ~ $ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

If you look into the history of apache, it was traditionally put in /usr/sbin and the page tree traditionally put in /var/www.

I don't remember if /srv came from Unix legacy or if it was recently added, but it is not used extensively.

/opt directory is typically where you find googleearth, chrome, games, etc.  Things that are binary blobs, or not open source, or not part of a traditional linux installation end up in /opt.  Many times, these same programs will be installed in your home directory, but then they are not available to other users as a system-wide installation.

So if you research each package, you will find its history and traditional installation location.  As long as the package conforms to some loose guidelines, it will install wherever the package maintainers decide to put it.

---

### Post by slickymaster on 2014-06-02
Moved to the **Server Platforms** sub-forum.

**/var** is for variable data files. This includes spool directories and files, administrative and logging data, and transient and temporary files.
**/srv** is for site-specific data which is served by this system.

---

### Post by sim085 on 2014-06-02
> **slickymaster said:**
> Moved to the **Server Platforms** sub-forum.

**/var** is for variable data files. This includes spool directories and files, administrative and logging data, and transient and temporary files.
**/srv** is for site-specific data which is served by this system.

So wouldn't it be more conformant with those description if these where located in **/srv/www**? Isn't apache2 serving html pages?
I do not see a static html page (or even a php page for that) as variable data, logging data or a temporary file.

---

### Post by slickymaster on 2014-06-02
> **tgalati4 said:**
> Directory assignments in linux are suggestions.  You can install any package anywhere.  As long as you have the correct permissions and the correct $PATH statement your programs will run.<...snip...>

This ^^^

---

### Post by sim085 on 2014-06-02
> **tgalati4 said:**
> Directory assignments in linux are suggestions.  You can install any package anywhere.  As long as you have the correct permissions and the correct $PATH statement your programs will run.

Ok, so if you had to install a program would you install this in /opt ? or /usr/bin ? or /usr/local/bin ?
What would you question yourself before taking such a decision?

---

### Post by tgalati4 on 2014-06-02
/usr/bin has traditionally been reserved for system files provided by your distribution.  Don't mess with them.  Don't add your stuff to them.  /usr/local/bin is for compiled programs (binaries) that you have created yourself, for use by anyone on that particular machine--system-wide availability.  It also contains convenience scripts that have been added, but are not considered vital to system operation.  It is included in the default path statement I referred to earlier.  Look in your /usr/local/bin and see what is there:

> tgalati4@Mint14-Extensa ~ $ ls /usr/local/bin
apt  gnome-help  highlight  mint-md5sum  search  yelp


So if you have a handy script to automate some task, a good place is to put in /usr/local/bin so all users on that machine can use it.  If it is a personal script, then you can put it in ~/Projects/scripts, but then you must add that to your $PATH statement.

In my /opt:

> tgalati4@Mint14-Extensa ~ $ ls /opt
firefox  google  mint-flashplugin-11

So there is no question.  Don't mess with /usr/bin.  Don't change permissions; don't delete what you think are "extra" files; don't delete /usr.  I have seen all three of these Use Cases and they all have bad outcomes.

Unless your programs look like firefox, or chrome, or a proprietary game, or a flash plug-in, don't install your stuff to /opt.

You can install stuff to /usr/local/bin, because that is why it is there--system-wide access to locally-generated (or distribution provided) scripts and binaries.

If you describe the program that you are developing, then we can provide more specific guidance.  There are packaging guidelines that you can follow to help with your decisions.

[http://packaging.ubuntu.com/html/](http://packaging.ubuntu.com/html/)

[https://help.ubuntu.com/community/PythonRecipes/DebianPackage](https://help.ubuntu.com/community/PythonRecipes/DebianPackage)

[https://help.ubuntu.com/community/SoftwarePackagingFormats](https://help.ubuntu.com/community/SoftwarePackagingFormats)

---

### Post by sim085 on 2014-06-02
> **tgalati4 said:**
> 
If you describe the program that you are developing, then we can provide more specific guidance.

Thanks for your reply. I asked the question for general knowledge. I did write a script in python that updates the zone file with the public ip of the machine. I placed this in /opt as I saw this as "optional application". From your description the place of this file looks more to be /usr/local/bin. Is this so?

---

### Post by bab1 on 2014-06-02
> **sim085 said:**
> Thanks for your reply. I asked the question for general knowledge. I did write a script in python that updates the zone file with the public ip of the machine. I placed this in /opt as I saw this as "optional application". From your description the place of this file looks more to be /usr/local/bin. Is this so?

It's all spelled out here as to where you should put your scripts or general data: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

User specific scripts should be at ~/bin (your home dir).  Machine local system admin created scripts belong at /usr/local/<some-dir>
FYI: The original naming of usr came from: UNIX System Reasorces.  It doesn't stand for *user*.

---

### Post by sim085 on 2014-06-03
> **bab1 said:**
> 
FYI: The original naming of usr came from: UNIX System Reasorces.  It doesn't stand for *user*.

Thanks :) I never knew that and I must admit that /usr was confusing me. I'll have a look through the links provided.

---

