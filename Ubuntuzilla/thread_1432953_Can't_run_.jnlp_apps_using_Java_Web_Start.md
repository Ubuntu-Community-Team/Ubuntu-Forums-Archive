---
title: "Can't run .jnlp apps using Java Web Start"
date: 2010-03-18
forum: Ubuntuzilla
---

### Post by kendoori on 2010-03-18
Am running 9.10 w/FF 3.6 via Ubuntuzilla. I initially had issues with Java, but followed the instructions on the wiki and it is now properly detected and verified to be working via Java's website; however, I am no longer able to launch .jnlp files. Firefox properly detects that it should use Sun Java 6 Webstart to open the file, but complains as follows:

```
/tmp/play-1.jnlp could not be opened, because an unknown error occurred.
Try saving to disk first and then opening the file.
```

I have another system that has FF 3.5.8 and am able to run this applet properly there.

There is something broken regarding the config as it relates to .jnlp files

According to Java's detection app, here's how I'm configured:

Your Java configuration is as follows:  
Vendor: Sun Microsystems Inc. Version: Java 6 Update 18 
Operating System: Linux 2.6.31-20-generic-pae Architecture: i386

---

### Post by nanotube on 2010-03-18
does this happen with /all/ jnlp files, or just this one or some subset of them?

---

### Post by kendoori on 2010-03-18
I'm encountering this with applets served up by elluminate.com

See any of the recorded sessions on this page: [http://www.elluminate.com/demo/recorded_demos_list.jsp](http://www.elluminate.com/demo/recorded_demos_list.jsp)

I have nothing else to compare this too. I guess if I've been executing .jlnp files previously they happened in the background and never was aware of them. I tried looking for other examples on the web, but haven't found one yet (though I'm sure they are common)

---

### Post by nanotube on 2010-03-18
well, the thing is, i have no idea here. so i was just trying to narrow it down to "problems with some particular jnlp and ff36", or "problems with all jnlp and ff3.6". 

but either way, i can't really think of anything to offer. try asking on the mozilla support forums, maybe.

---

### Post by javanadu on 2011-04-07
What is your mime type. Are you hosting the webstart application. If you are hosting the application you probably don't have the good mime type mapping 

Do you have something like :

```
application/x-java-jnlp-file   jnlp 
```

More info at **[[COLOR="DarkRed"]Java Webstart troubleshooting[/COLOR]]("http://www.java-tutorial.ch/build/webstart")**

---

### Post by Karlchen on 2011-04-08
Hello, kendoori.

Just today, I experienced the same problem as you reported, no matter whether I tried to launch a Java application through a .JNLP file using Firefox 3.6.16, Firefox 4.0 or Opera 11.01. I kept on receiving the same kind of error message that you reported  > /tmp/play-1.jnlp could not be opened, because an unknown error occurred.
Try saving to disk first and then opening the file.Even if I did save the .JNLP file to disk, right clicked it in Nautilus and selected to open it using "Sun Java 6 Web Start", this did not work and I recceived an error message stating that "the file" could not be found. No detail given which file might be "the file".

[U]Environment here:
[/U]Ubunto 10.04, 32-bit
Firefox 3.6.16 (Ubuntu build), Firefox 4.0 (Mozilla build), Opera 11.01
Oracle Java 6 Update 24

[U]Default action defined in
[/U]
[LIST]
[*]Nautilus: Open in "Sun Java 6 Web Start"
[*]Firefox / Opera: Open in "Sun Java 6 Web Start (Default)"
[/LIST]
[U]Note:
[/U]Launching .JNLP files in Nautilus and the browsers had still worked a few weeks ago.

[U]Investigation steps:
[/U]OK, I'll cut those short and report the results only: Google is my friend. So are the Ubuntu help and forum pages. :D

_Source of trouble:_

The Gnome desktop defines the actions which will be performed on file types in a file named **mimeapps.list**, located in the folder **~/.local/share/applications**.
```
grep jnlp mimeapps.list
application/x-java-jnlp-file=sun-java6-javaws.desktop
```So the action for 'Open in "Sun Java 6 Web Start"' must be defined in a file named **sun-java6-javaws.desktop**.
```
~/.local/share/applications$ cat sun-java6-javaws.desktop
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=Sun Java 6 Web Start
Comment=Sun Java 6 Web Start
Exec=/usr/lib/jvm/java-6-sun-1.6.0.22/jre/bin/javaws %u
Terminal=false
Type=Application
Icon=sun-java6
Categories=Application;Network;
MimeType=application/x-java-jnlp-file;
```Arghh. There it is: **Exec=/usr/lib/jvm/java-6-sun-1.6.0.22/jre/bin/javaws %u**
This line still references the no longer existing Java 6_22 version.
So the line should read: **Exec=/usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/javaws %u **or even better to prevent the same error from re-occurring after the next Java update: [B]Exec=/usr/bin/javaws %u

[/B]_Solution:_
Modified the file sun-java6-javaws.desktop to read ```
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=Sun Java 6 Web Start
Comment=Sun Java 6 Web Start
Exec=/usr/bin/javaws %u
Terminal=false
Type=Application
Icon=sun-java6
Categories=Application;Network;
MimeType=application/x-java-jnlp-file;
```[U]Testing:
[/U]Launched Firefox and downloaded the .JNLP file to disk. Right clicked it in Nautilus and selected "Open with Sun Java 6 Web Start". The application was launched without problems.

Launched Firefox and selected to have Firefox to "Open with Sun Java 6 Web Start (Default)". The application was launched without problems.

[U]Status:
[/U]Problem solved.

HTH,
Karl

---

### Post by zwigno on 2011-07-21
I changed the line to:
```
Exec=/usr/lib/jvm/java-6-sun/bin/javaws %u
```
This should be a more permanent fix since java-6-sun should always point to the current version.  I noticed the line was also off in sun-java6-java.desktop so you may want to fix that too.

---

### Post by gcordoba on 2012-08-17
There is a problem in firefox as java-sun is now blocked due to security issues.

If you still cannot use Elluminate, perhaps my experience helps:

[http://ubuntuforums.org/showthread.php?p=12178476#post12178476](http://ubuntuforums.org/showthread.php?p=12178476#post12178476)

---

