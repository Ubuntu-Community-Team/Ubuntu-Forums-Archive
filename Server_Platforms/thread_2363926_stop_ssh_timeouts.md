---
title: "stop ssh timeouts"
date: 2017-06-16
forum: Server Platforms
---

### Post by micahpage on 2017-06-16
I would like to stop ssh timeouts as they are very annoying. Especially if using the server as a proxy. I guess i would prefer to have the client do it to keep the server as secure as possible, but i would like to know how to do that as well.

on this site
[https://www.bjornjohansen.no/ssh-timeout](https://www.bjornjohansen.no/ssh-timeout)

it says to add the line **ServerAliveInterval 120 **to [B]~/.ssh/config
[/B]However there is nothing in my local at all for config
```
metulburr@ubuntu:~/.ssh$ 
lsknown_hosts

```

---

### Post by Habitual on 2017-06-16
```
vi .ssh/config
``` will create it.

and it's 
```
ls ~/.ssh/known_hosts
```
or
```
ls known_hosts
```
if you in /home/<user>/.ssh/

I have these values from my desktop client for over 5 years.
```
Host *
IdentitiesOnly yes
ServerAliveInterval 120
ServerAliveCountMax 30
ConnectTimeout 30
UseRoaming no
```

Only things done on the server side are the usual [StricterDefaults]("https://help.ubuntu.com/community/StricterDefaults#SSH_Settings")
~/.ssh/known_hosts should be 600
Check that with
```
stat --printf "%a %n \n" ~/.ssh/known_hosts
```

Have fun.

---

### Post by TheFu on 2017-06-16
tmux not an option?

The ~/.ssh/config file is something you create.  Start typing. The ssh_config manpage is very good, BTW.  It is very handy for alternate userids, aliases instead of IPs and especially for non-standard ports.  It is honored by every libssh tool I've found - ssh, scp, sftp, rsync, rdiff-backup, sshfs, .... you get the idea.  A very useful config file.

---

### Post by micahpage on 2017-06-16
oh ok. I didnt know you had to manually create it. Normally there is default files filled out with commented out examples of such things.

> [COLOR=#000000]and it's [/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=&amp]ls ~/.ssh/known_hosts[/FONT][/COLOR]
Yeah i know. This forum's code box seems to mess up the output from a terminal.


[ATTACH=CONFIG]275662[/ATTACH]
but then it gets auto formatted to the following after hitting submit
```
metulburr@ubuntu:~/.ssh$ lsknown_hosts



```

EDIT:
I had to use an outside source to upload images to because this forums is showing the attachments in the post, but not visible when live. So whatever. I give up trying to dicker with the attachment manager. The following images are of what i am copying and what i am inputting into the editor....however what i input is not what shows up. 
[http://imgur.com/a/U7WzM](http://imgur.com/a/U7WzM)

---

### Post by TheFu on 2017-06-16
So, is this solved? If so, please mark the thread as such to help the community out. It helps both the askers and the answerers. ;)

We generally don't use attachments.  cmds are clearer and tiny. Good for people with limited bandwidth.  Plus I can select/paste YOUR text and edit it. Can't do that with an image. I won't. See you found the 'code tags', but the missing space seems odd. Probably a terminal issue, if it wasn't user-error.

In a pure xterm, select/paste is the method I use. Always works.  Notice, that is select/paste, not copy/paste.  Much faster too, but limited to only a single selection at a time and only works with programs that don't take over the x-buffer.

---

