---
title: "Require Password to Run a Program"
date: 2008-08-15
forum: Security
---

### Post by ExodusC on 2008-08-15
Hi guys, I'm curious as to if there is a way to require a password to run a program.  More specifically I'd like to require a password to run any program under Wine (requiring the sudo password would be great).

This isn't a public computer, but I have family members that use it from time to time, and I don't want them installing anything (Windows programs of course) with Wine that I wouldn't want installed.

Is there any easy way to do something like this?

---

### Post by wilbbe01 on 2008-08-15
I'm not sure if it would work or not, but you could try changing permissions so the user your family uses doesn't have permission to wine.  Taking away execute permissions for everyone but root, and giving root ownership would only allow root/sudo to run it, but not sure as to whether or not that would cause things to fail in weird ways or not.

---

### Post by ExodusC on 2008-08-15
> **wilbbe01 said:**
> I'm not sure if it would work or not, but you could try changing permissions so the user your family uses doesn't have permission to wine.  Taking away execute permissions for everyone but root, and giving root ownership would only allow root/sudo to run it, but not sure as to whether or not that would cause things to fail in weird ways or not.
Hmm, that might work.

I only actually have a single user on this box because it's usually just myself using it, but I wouldn't mind having to type in a password to run a Windows program, as I really don't do it that often on that box.

Mind giving a brief explanation (or linking to a tutorial) on how to change permissions for it?  Sorry, I'm really not that experienced with Linux to be honest.

---

### Post by wilbbe01 on 2008-08-15
Ok, yeah I'll try to help you with how I would try it, but I can't say for sure if it would screw things up or not.  I'm currently working on reinstalling my OS's so they can be sparkly clean again, but I'll try my best remembering here from windows.

I'll assume you know how to change directory from the command line.  Go to the directory of wine, or maybe the shortcut of a program you want to require a password.

Once in that directory you can type

```
ls -lh
```

you will notice on the left side a series which looks something like the following list.

drwxr-xr-x   2 owner group  232 2008-06-20 00:23 dir name
-rwxr-xr-x   1 owner group  559 2008-02-27 20:04 file name

You'll notice the first row has a d at the front and followed by 9 characters.  The d means it is a directory and the characters are the permissions.  The first set of 3 characters after the d (or - in the second line) denotes the owner permissions (see "owner" to see who that user might be.  The second set of three is for the group (see "group" to see who that group may be).  Lastly the third set is for everyone.

Now for the changing.  Type the following to change the owner of a file or directory.

```
chown [new owner] [name of file/directory]
```

If I was doing this I would try with setting owner to root, then removing execute permissions for the group and everyone.  To set root use the previous command and place "root" in place of [new owner].  The following command will give the owner read, write, and execute power and give everyone else no power.

```
chmod 700 [name of file]
```

That command will give access to the owner only (in this case a requirement to be root.  You will have to start things from the command line so you can give root access to start it, so the gui buttons probably won't work.

The 700 above basically means give owner everything, group nothing, and everyone nothing.

Does that make any sense?  I can't verify this won't screw things up, but it is what I would try.  Sorry I can't test out what I just said myself right now, ask me any questions you may have and I'll try my hardest to answer them for you.  Good luck.

---

### Post by DGortze380 on 2008-08-15
> **ExodusC said:**
> Hmm, that might work.

I only actually have a single user on this box because it's usually just myself using it, but I wouldn't mind having to type in a password to run a Windows program, as I really don't do it that often on that box.

Mind giving a brief explanation (or linking to a tutorial) on how to change permissions for it?  Sorry, I'm really not that experienced with Linux to be honest.

Changing permissions for wine probably isn't the best idea, it could cause some flaky problems. I wold suggest creating a new user account. Edit sudoers to give them sudo access to what they need but not anything else.

---

### Post by wilbbe01 on 2008-08-15
if you only change permissions on the one file how is always running it as sudo going to cause flaky performance?  I guess security sounds iffy, but I'm not sure I see why running it as a user with permission to is going to be any different than it is now.  The user you are running it as will have full permission, how is that any different than having a different user with x permission?

---

### Post by Perkins on 2010-12-25
Some wine programs do not play nicely with your system if they have root privileges.

Some (very few) wine programs do not run without root privileges.

I would change the user to something other than root and deny execute to other users.  Then you can use 'sudo -u <usernamd> <command> to run wine as that, nonprivileged user.

Sudo actually has a lot of nifty features.  I would suggest at least skimming man sudo at some point.  Also man bash and man man.  ;)

---

### Post by cariboo on 2010-12-25
This thread is 2 years old, the op hasn't been back since Aug. 2008. Closed

---

