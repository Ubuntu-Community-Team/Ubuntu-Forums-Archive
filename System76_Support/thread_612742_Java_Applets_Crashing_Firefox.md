---
title: "Java Applets Crashing Firefox"
date: 2007-11-14
forum: System76 Support
---

### Post by rdemars on 2007-11-14
I have 7.10 installed on my Gazelle with Firefox 2.0.0.8 and Java(TM) Plug-in 1.6.0_03 installed.  Every time I browse to a web page that has a Java applet on it, the Firefox application crashes and disappears.  It even happens when I start Firefox with the -safe-mode option.  An example site is Java test page at: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

If I start Firefox from the command prompt I get these errors:
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success
INTERNAL ERROR on Browser End: SendRequest: write failed. Dead VM? 32
System error?:: Broken pipe
INTERNAL ERROR on Browser End: Plugin instance index out of bounds 31408
System error?:: Success

If anyone has any ideas on this issue, I would be most appreciative.

---

### Post by thomasaaron on 2007-11-14
I've not experienced this myself, but there are a ton of posts on the web saying that something is wrong with the java6 plugin.

Many people have reported that moving back to the java5 plugin fixes the problem.

So, you might try...

sudo apt-get remove sun-java6-plugin
sudo apt-get install sun-java5-plugin

...and then restart your browser.

---

### Post by rdemars on 2007-11-14
Thanks for the reply.  I have tried that with no luck.  I have even gotten the Java and Firefox straight from their websites, all still with no luck.  To me it is starting to look like a Java issue trying to access the libc.so.6 library.  I finally was able to get a Java error log file from one of the crashes:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7eb2cbc, pid=14336, tid=3034065808
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x71cbc]  memcpy+0x1c
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0xb5ade800):  JavaThread "Thread-4" [_thread_in_native, id=14359]

siginfo:si_signo=11, si_errno=0, si_code=2, si_addr=0xb4d32000

Registers:
EAX=0xb5261001, EBX=0xb7f86ff4, ECX=0x0000021e, EDX=0x00000fff
ESP=0xb4d016f0, EBP=0xb4d01714, ESI=0xb5261788, EDI=0xb4d32000
EIP=0xb7eb2cbc, CR2=0xb4d32000, EFLAGS=0x00210207

Top of Stack: (sp=0xb4d016f0)
0xb4d016f0:   b7e9afda b4d31879 b5261001 00000fff
0xb4d01700:   b4d31879

---

### Post by rdemars on 2007-11-15
JRE tries to call the libnss_files.so library to find localhost name and it forwards it onto the libc.so.6 file.  If the localhost entry in the host file is too long, it will crash the JRE.  It appears that on my system, the Network Manager Application had grouped all my 127.0.0.1 localhost entries (used to block spyware and adware sites) into one 127.0.0.1 line.  The 127.0.0.1 in my host file was huge.  I separated the line back out into individual lines and the JRE started working again.

---

### Post by porschify on 2007-11-17
An upgrade to Firefox 2.0.0.9 has solved most of my freezing problems in gutsy.

---

### Post by Squish42 on 2008-02-28
I had a similar problem and chanced into a solution here: [http://www.getautomatix.com/forum/index.php?showtopic=1653](http://www.getautomatix.com/forum/index.php?showtopic=1653)

In a nutshell, my hosts file was corrupted.  I remember trying to open it in Network settings recently and it must have reformatted the file.  I use the 127.0.0.1 file from [http://www.mvps.org/winhelp2002](http://www.mvps.org/winhelp2002) which creates a very large hosts file.

With the file back to normal, Firefox is working perfectly.

---

### Post by feeshy on 2008-06-18
Thank you all!

I've reinstalled and reconfigured every browser and java configuration I could find and finally found this thread and fixed the problem :)

It was the hosts file:

[http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)

..which I must have edited with an editor that stripped out the line-breaks....

---

