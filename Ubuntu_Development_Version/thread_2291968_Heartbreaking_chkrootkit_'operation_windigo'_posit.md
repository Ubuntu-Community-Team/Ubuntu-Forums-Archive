---
title: "Heartbreaking chkrootkit 'operation windigo' positive warning"
date: 2015-08-24
forum: Ubuntu Development Version
---

### Post by fthx on 2015-08-24
Hi,

Was raining today but suddenly I got the sun in my face :

```
sudo chkrootkit

Searching for Linux/Ebury - Operation Windigo ssh...        Possible Linux/Ebury - Operation Windigo installetd
```

(original typo...)

8-[

Well... after some search I think it's a false positive. (I do not play with fishy PPAs and do not use my system as a server.) 
Sources :
[http://www.eset.com/int/about/press/articles/article/operation-windigo-largest-server-botnet-uncovered/](http://www.eset.com/int/about/press/articles/article/operation-windigo-largest-server-botnet-uncovered/)
[https://www.cert-bund.de/ebury-faq](https://www.cert-bund.de/ebury-faq)
[http://ubuntuforums.org/showthread.php?t=2288339&highlight=operation+windigo](http://ubuntuforums.org/showthread.php?t=2288339&highlight=operation+windigo)
[https://bbs.archlinux.org/viewtopic.php?id=195395](https://bbs.archlinux.org/viewtopic.php?id=195395)
[https://github.com/openssh/openssh-portable/commit/957fbceb0f3166e41b76fdb54075ab3b9cc84cba](https://github.com/openssh/openssh-portable/commit/957fbceb0f3166e41b76fdb54075ab3b9cc84cba)

If you run the "ssh -G" test in above links, you could be scared. But the commit (link to github) seems to show that a new ssh option has been introduced since the testing command line :
```
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected"
```
So this command does not return any error message, so you should get "System infected" in your terminal...

I checked the sizes of the libraries (2nd link), ran ipcs commands and everything seemed to be ok.

What do you think about this stuff ? Should I run some additional tests ?

---

### Post by QDR06VV9 on 2015-08-24
I would think you would be safe if you did not show [COLOR=#000000][FONT=Ubuntu Mono]"System infected"

Also there is this to show if infected.
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Courier New]# netstat -nap | grep "@/proc/udevd"[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] 

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]> **Ebury version 1.5**[/FONT][/COLOR]> 
[COLOR=#000000][FONT=Verdana]On Linux-based systems, an additional shared library file 'libns2.so' is installed and the existing libkeyutils file is patched to link against this library instead of libc6. The malicious 'libns2.so' file can be located by running the following command, which should not return any results on clean systems.[/FONT][/COLOR]
# find /lib* -type f -name libns2.so
/lib64/[COLOR=#FF0000]libns2.so[/COLOR] [COLOR=#000000][FONT=Verdana]Ebury now uses Unix domain sockets instead of shared memory segments for interprocess communication. _**The malicious socket can be located using 'netstat' as follows.[COLOR=#0000ff] Again, this command should not return any results on clean systems[/COLOR].**_[/FONT][/COLOR]

> [COLOR=#000000][FONT=Verdana]**Do antivirus products or other security tools detect Ebury?**[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Some antivirus products are capable of detecting Ebury, usually as 'SSHDoor' or 'Sshdkit'. However,**ClamAV or tools like chkrootkit or rkhunter currently do not detect Ebury**.[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]For Me
[/FONT][/COLOR]```
me-Aspire-M3300 me # netstat -nap | grep "@/proc/udevd"
me-Aspire-M3300 # exit
exit
me@me-Aspire-M3300:~$ ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected"
System clean

```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hope that helps:)
Regards[/FONT][/COLOR]

---

### Post by fthx on 2015-08-24
I already searched the libns2.so file and it gave me nothing. The netstat command does not return anything, as wished.

Are you running Wily ? On another PC with Trusty, the command 'ssh -G' gives me an error, but not on my PC running Wily. Is it really related to the commit (link in my previous message) ?

---

### Post by QDR06VV9 on 2015-08-24
> **fthx said:**
> I already searched the libns2.so file and it gave me nothing. The netstat command does not return anything, as wished.

Are you running Wily ? On another PC with Trusty, the command 'ssh -G' gives me an error, but not on my PC running Wily. Is it really related to the commit (link in my previous message) ?
I am Strictly Linux, and run both Wily and Trusty, and both produce the same results(Clean).
You have me curious though What Error Showed?  (with the [COLOR=#000000]the command 'ssh -G' )
Take into consideration that [/COLOR][B]ClamAV or tools like chkrootkit or rkhunter currently do not detect Ebury.
Atleast with [/B]chkrootkit version 0.49
SSH Version on trusty not on wily ATM
```
apt-cache policy sshssh:
  Installed: (none)
  Candidate: 1:6.6p1-2ubuntu2.3
  Version table:
     1:6.6p1-2ubuntu2.3 0
        500 http://mirror.internode.on.net/pub/ubuntu/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:6.6p1-2ubuntu1 0
        500 http://mirror.internode.on.net/pub/ubuntu/ubuntu/ trusty/main amd64 Packages



```

---

### Post by fthx on 2015-08-24
It's chkrootkit v. 0.50 in Wily. It does have a Ebury suspicion detection (I do not know ho it does that).

It's curious that you ask for my (Trusty) error message resulting from 'ssh -G' since it's this error message which is simply detected by the command line : 
[FONT=courier new]ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected" .[/FONT]

In Trusty, I get one line with an error message and some other lines with ssh available options. In Wily I just get ssh available options. The commit in openssh I linked above is implemented in Wily's openssh : 
[FONT=courier new]"ssh(1): Add a -G option to ssh that causes it to parse its configuration and dump the result to stdout, similar to "sshd -T" [/FONT]
in version 1:6.9p1-1.
Do you run this version ?

---

### Post by fthx on 2015-08-24
Ooookay, I get it.

In :
[https://github.com/Magentron/chkrootkit/blob/master/chkrootkit](https://github.com/Magentron/chkrootkit/blob/master/chkrootkit)
I found line 1137 in [FONT=courier new]chkrootkit[/FONT] file :
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]## SSJD Operation Windigo  (Linux/Ebury) 
[/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]   if [ "${QUIET}" != "t" ]; then[/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]      printn "Searching for Linux/Ebury - Operation Windigo ssh... "; fi[/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]   if $ssh -G 2>&1 | grep -e illegal -e unknow > /dev/null; then [/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]      if [ "${QUIET}" != "t" ]; then echo "nothing found"; fi[/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]   else[/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]         echo "Possible Linux/Ebury - Operation Windigo installetd" [/FONT][/TD]
                                [TD="class: blob-code blob-code-inner js-file-line"][FONT=courier new]   fi  [/FONT][/TD]
[/TR]
[/TABLE]
Copy and paste is a big mess here, but I can check the detection method, which is the [FONT=courier new]ssh -G 2>&1 ([FONT=book antiqua]etc.) trick.[/FONT][/FONT]

Sooooo : it seems to me to be solved. I wait for an expert to change the subject of this thread.

---

### Post by Eriamieka on 2015-11-28
Hey all,
When I run:
sudo netstat -nap | grep "@/proc/udevd"   I get nothing, when I search for libns2.so, no result too. But when I run:
ssh -G 2>&1 | grep -e illegal -e unknown > /dev/null && echo "System clean" || echo "System infected" answer is system infected, when I then run:
sudo chkrootkit on Ebory's search it says: Possible Linux/Ebury - Operation Windigo installetd
Version of SSH:
ssh:
  Installed: 1:6.9p1-3
  Candidate: 1:6.9p1-3
  Version table:
 *** 1:6.9p1-3 0

How can I make sure my system is infected or not? Already made a clean install to realize that the answers were the same.
Thanks in advance.

---

### Post by cariboo on 2015-11-28
@Eriamieka , I'd suggest you start a thread in the Security sub-forum, as this one has nothing to do with Xenial. Thread Closed

---

