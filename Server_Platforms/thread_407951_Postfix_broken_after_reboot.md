---
title: "Postfix broken after reboot"
date: 2007-04-12
forum: Server Platforms
---

### Post by lassel on 2007-04-12
I have a small personal mailserver with postfix and courier. It has worked flawlessly since I installed it a few months back.

After a restart postfix didn't come up. [I]
I need a little help getting it back up. Solutions or suggestions on how to find out what is wrong is most welcome.[/I]

I get this message when I attempt to start it:

```

lasse@enoch:/etc$ sudo /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix                                                                       postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)

```

I tried to reinstall postfix, without luck.

```

lasse@enoch:/etc$ sudo apt-get install postfix --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  courier-imap libfam0 courier-ssl courier-base courier-authlib-userdb courier-authlib courier-authdaemon libltdl3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1067kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 18124 files and directories currently installed.)
Preparing to replace postfix 2.3.3-1 (using .../postfix_2.3.3-1_i386.deb) ...
 * Stopping Postfix Mail Transport Agent postfix                                                                [ ok ] 
 * Stopping Postfix Mail Transport Agent postfix                                                                [ ok ] 
Unpacking replacement postfix ...
Setting up postfix (2.3.3-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

in master.cf:
  adding missing entry for tlsmgr service
  adding missing entry for scache service
  adding missing entry for discard service
Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                                                                [ ok ] 
 * Starting Postfix Mail Transport Agent postfix                                                                       postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)
                                                                                                                [fail]
invoke-rc.d: initscript postfix, action "restart" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by BitHosts on 2007-04-12
what happens when you run:

/etc/init.d/postfix restart

?

---

### Post by lassel on 2007-04-13
Well... since I can't start the process restarting it does nothing for me. I get the same message as above when I try starting it.

#sudo strace /etc/init.d/postfix start

Trying strace gives me:
(note the red block near the end)

I can't decipher it, any ideas?

```

clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7ea86f8) = 5909
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/dev/pts/0\n", 128)            = 11
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5909
stat64("/usr/bin/tput", {st_mode=S_IFREG|0755, st_size=9320, ...}) = 0
geteuid32()                             = 0
)                       = 1
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7ea86f8) = 5910
                                                                                                                                                          --- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5910
write(1, "[", 1[)                        = 1
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7ea86f8) = 5911
[COLOR="Red"]--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5911
write(1, "fail", 4fail)                     = 4
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7ea86f8) = 5912
[/COLOR]--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5912
write(1, "]\n", 2]
)                      = 2
exit_group(1)                           = ?
Process 5863 detached

```

---

### Post by BitHosts on 2007-04-13
Sorry mate - thats past my limit for the moment. Good luck

---

### Post by bmathis on 2007-04-13
After you uninstalled did you remove all the directories and files that postfix might of left behind?

Also, you should consider using the aptitude command instead of apt-get, it will automatically remove any dependencies and whatnot when ever you remove a program, apt-get does not.

---

### Post by derwisch on 2007-06-27
In the meantime, it has been filed as a bug:

[https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/56235](https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/56235)

---

