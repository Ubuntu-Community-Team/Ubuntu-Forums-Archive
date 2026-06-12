---
title: "Ejabberd on Edgy Server"
date: 2006-11-28
forum: Server Platforms
---

### Post by dnel on 2006-11-28
There appears to be a bug on Edgy between ejabberd and erlang r11 which means ejabberd is completely unusuable and difficult even to uninstall. Using erlang to r10 should fix the problem but is there an easy way to install an older version on my server within apt-get or will i need to downgrade to Dapper server? If the latter, any advice on how to do that or is it as simple as change the apt.sources like usual?

TIA
dnel

---

### Post by fromvega on 2007-01-03
Hello,

I'm having problems with ejabberd too, the problem is "hostname: Unknown host". I have configured it to localhost but the error persists.

I have tried to uninstall it and I've got the following errors.
Have you succeded unistalling it? Could help-me?

Thank you!

Removing ejabberd ...
hostname: Unknown host
RPC failed on the node ejabberd@: nodedown
dpkg: error processing ejabberd (--remove):
 subprocess pre-removal script returned error exit status 3
Starting jabber server: ejabberdhostname: Unknown host
.
Errors were encountered while processing:
 ejabberd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dnel on 2007-01-04
I resolved my problem by removing Edgy and installing a clean copy of Dapper instead which worked. 

The problem you're having is the pre-remove script which is trying to use the daemon for cleaning up and failing for the same reason it won't run. 

To get around this you need to edit  /var/lib/dpkg/info/ejabberd.prerm

Remove the following code between the two comments and save the file.

```

# Automatically added by dh_installinit
if [ -x "/etc/init.d/ejabberd" ]; then
        if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
                invoke-rc.d ejabberd stop || exit 0
        else
                /etc/init.d/ejabberd stop || exit 0
        fi
fi
# End automatically added section


```

Try removing again using apt-get and that should do the trick. Make sure you kill any remaining processes that might be running.

---

### Post by fromvega on 2007-01-04
Hello,

thank you for your answer! I have changed the hostname of my machine because I realized that it was incosistent in some way. I also have tried to do what you have told me withouth sucess. Now I'm receving the following error when trying to remove ejabberd.

Do you have any idea to solve it?
Thank you in advanced!


Removing ejabberd ...
Can't store backup in "/var/tmp/ejabberd-database.tdahPr4083" at node ejabberd@bigboy: {"Cannot prepare checkpoint (replica not available)",
                                                                                        [config,
                                                                                         {{1167,
                                                                                           931470,
                                                                                           486367},
                                                                                          ejabberd@bigboy}]}
dpkg: error processing ejabberd (--remove):
 subprocess pre-removal script returned error exit status 1
Starting jabber server: ejabberd.
Errors were encountered while processing:
 ejabberd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dnel on 2007-01-04
There is additional parts to that script which back up your user database which need to be removed. I don't believe this is in the dapper version of the script which I was using for reference. You'll need to locate this part and remove it also, from what I remember its fairly clear from the remarks to show where it is.

---

### Post by fromvega on 2007-01-05
Thank you!

---

