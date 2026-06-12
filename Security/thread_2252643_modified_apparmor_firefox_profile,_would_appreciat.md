---
title: "modified apparmor firefox profile, would appreciate if experts could comment"
date: 2014-11-13
forum: Security
---

### Post by a-you on 2014-11-13
I switched from using the nouveau graphics driver to using the nvidia driver because I wanted to try the shotcut video editor and that wouldn't work so long as I was using the nouveau driver. With the nvidia driver though apparmor started putting up notifications of 6 "DENIED" events. Apparently /usr/lib/firefox/firefox.sh is a script that was trying to read /proc/modules and /proc/driver/nvidia/params and also there was (I think) a lock file being created in ~/.nv/GLCache/ which that script wanted rw access to.

So I added these lines to /etc/apparmor.d/usr.bin.firefox

  @{PROC}/modules/ r,
  @{PROC}/modules/* r,
  @{PROC}/driver/nvidia/params/ r,
  @{PROC}/driver/nvidia/params/* r,
  /home/myusername/.nv/GLCache/* rw,

The duplication in the 2 @{PROC} lines is because I'm not sure what I'm doing. My reasoning behind the above changes was that after all the profile already contains this:

  # These are needed when a new user starts firefox and firefox.sh is used
...
  @{PROC}/ r,

so I figured there'd be no harm in adding read access specifically for those subfolders of /proc

If anybody that knows more about this than I do (probably a lot of you do) might comment, just to tell me if this was wrong or if there's a more appropriate way to do it, I'd much appreciate it.
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
sudo service apparmor reload
Thanks in advance!!!

I'm using ubuntu studio 14.4 trusty 64 bit.

[edit] less clear than ever: the above works for the first new window opened by firefox after doing

```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
sudo service apparmor reload
```

but for each window after that the errors are back. I don't understand this at all.

Any help would be much appreciated, thank you.

---

### Post by fugu2 on 2014-11-15
> **a-you said:**
> The duplication in the 2 @{PROC} lines is because I'm not sure what I'm doing. 
Im not an apparmor expert, but I think I understand the difference for the ALMOST duplicate lines.
the line without the star @{PROC}/ means that you allowing the protected program to read whats just inside that specific directory, as in just read the names of the files, but it doesn't give read access to those files.
the star @{PROC}/* allows read access to the files (and directories, i think) inside that directory.
a double star @{PROC}/** means regressive read access to all files and directories from that directory on.

---

### Post by a-you on 2014-11-24
Thanks[**[COLOR=#000000] fugu2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1903839") for your comments. What you say makes sense, and I thought so too, but no matter what I tried apparmor was still blocking the same things. In the end I went back to using the nouveau driver. I didn't mark the thread as solved because as far as I'm concerned it isn't solved, and I didn't come up with anything that might help others.

---

### Post by fugu2 on 2014-11-27
You could try to put the profile into complain mode
```
sudo aa-complain /usr/bin/firefox
```
Warning: This will remove the protections that apparmor provides temporarily, so that it can gather the required permission requests.
You'll need to use the web browser at this point to force it to attempt various requests. (i.e. trying to open test.html on your Desktop will log a request ~/Desktop/test.html 'r')
```
sudo aa-logprof
```
This will scan the apparmor log files and let you set permissions via a cli ui.
```
sudo aa-enforce /usr/bin/firefox
```
This will re-enable the new profile, and remove the complain mode

---

### Post by a-you on 2014-11-28
Thanks again for your comments. At the moment I'm back to using the nouveau driver so apparmor is no longer blocking things that it started blocking when I switched to the nvidia driver. Unless I switch the driver again it'd be hard to further explore that issue, and at the moment I don't have time to switch back just to do this debugging (deadline :-( ). I may go back to the nvidia driver at some point when I have more time.

Btw I seem to recall reading somewhere that one of the "aa-" tools was broken in trusty, but a quick search just now doesn't show me what that might have been. (And maybe it's a wrong impression!)

In any case, thanks a lot for offering to help!!

---

### Post by a-you on 2015-05-13
In case it helps somebody I came back to this and seem to have solved it.

I re-enabled the nvidia driver and again apparmor was putting up notifications each tiime I'd open a new firefox window. I edited the apparmor profile for firefox by adding these lines and so far so good:

```
  /proc/modules r,
  /proc/modules/ r,
  /proc/modules/* r,
  /proc/modules/** r,
  /proc/driver/nvidia/params r,
  /proc/driver/nvidia/params/ r,
  /proc/driver/nvidia/params/* r,
  /proc/driver/nvidia/params/** r,
  owner @{HOME}/.nv/GLCache/ k,
  owner @{HOME}/.nv/GLCache/* k,
  owner @{HOME}/.nv/GLCache/** k,

```

It possible (likely) that I overdid it, addiing slightly more than necessary, but it's fine with me if so.

---

