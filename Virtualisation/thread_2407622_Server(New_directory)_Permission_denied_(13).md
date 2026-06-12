---
title: "Server(New directory) Permission denied (13)"
date: 2018-12-06
forum: Virtualisation
---

### Post by juuchijs on 2018-12-06
**Hello!**

I am installing Ubuntu Server for Uni project and now I'm having difficulties to understand how to fix this problem I have.

So I do: ```
sudo apt install mc
```, then I type ```
mc
``` and it opens, then I press *F7* to create new directory, when I type the name of directory I get message- [I]Permission denied (13).
[/I]

Probably the fix for this is very simple but I'm new to Linux.
[ATTACH=CONFIG]281893[/ATTACH]

[ATTACH=CONFIG]281894[/ATTACH]

Hoping to get some help guys!


Maybe someone could please explain me, where is my mistake?

---

### Post by SeijiSensei on 2018-12-06
You can only create files and directories in a limited number of places.  If you navigate to your home directory, /home/julijs, you should have no problems creating a directory there.

Please read this documentation about how permissions work in *nix: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You might need to read it a couple of times if you're new to Linux.

---

### Post by juuchijs on 2018-12-07
[ATTACH=CONFIG]281895[/ATTACH]

*professor sample

Ok, thank you! This is my example, but my professor is creating folder not in home directory. Does I have to enable Root, to create that specific folder? Because under my name -julijs I managed to create folder, but I think I have to make new folder where I dont have permission.

So to do that I have to login in with: sudo -i and then I have to type password, after that I have to type mc and then can I create that folder? Is it correct?[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]

---

### Post by slickymaster on 2018-12-07
@juuchijs:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by SeijiSensei on 2018-12-07
I don't know why any "professor" would tell you to create a folder directly under /home.  The only directories that belong there are the ones for each user on the system.

The only way you can create a directory under /home would be as the root user using sudo.

---

### Post by juuchijs on 2018-12-07
I think like that, because in that last photo I uploaded in the bottom there is root@ig123489:/home# 

So that means I have to use sudo to achieve that?

---

### Post by SeijiSensei on 2018-12-07
Leave Midnight Commander aside and just use the command prompt:

```
sudo mkdir /home/nameofthedirectory
```

---

### Post by TheFu on 2018-12-07
+1 on forgetting mc and staying with the normal shell while learning.  Out of thousands of friends using Linux, I know only 1 who uses mc.

I suspect there's  a misunderstanding about what "home" means.  There are multiple meanings to that word, based on context.  In my Linux training classes, I go over the differences.  Let me see if I can find that slide .... 

```
Main Directories

-    HOME directory, $HOME, ~/ - all the same thing
-    root directory, / - top level of all files and directories
-    root HOME directory - /root - on Linux systems
-    /tmp - a temporary directory. Anyone/nobody can write there. Wiped at reboot
-    /bin, /usr/bin - where more programs are installed
-    /etc - where most system and package manager settings are stored
-    /usr/local/ - where non-package managed, but system-wide programs belong
```

---

### Post by JayKay3OOO on 2018-12-08
The owner of most of the file system is root for security reasons and then you have your own user which by default has ownership to home/user.

I'd get used to navigating the file system using the command line. It's not that hard once you get used to it and you won't be out of your depth when you don't have your special tool. The command line is always the same look and feel no matter the distro.

I guess if you don't know:

sudo - means to temporarily give your user root level of power. so when you sudo mkdir /wherever you are giving yourself temporary extra power to make that directory where you want. Aim is by not being root applications can't go crazy and eat your filesystem, but sometimes we need to overrule root so that's why sudo exists.

Remember that scene in the matrix where the guy is looking at code and pointing out objects like he can see real visuals by reading the code, in a command line environment, once you work out the general structure your mind will fill in the gaps and create a mental image of the system. So eventually you'll be seeing visuals in the vast code sea.

Stay watchful of peoples commands. I wouldn't sudo rm -rf /* - .... ...just sayin.

You can also easily change the owner of a folder by using the chown command - sudo chown  youuser /home  now youruser owns that folder and therefore has full power without the need to constantly sudo every time you want to do anything. You can also use the chmod command to keep the ownership as root and allow others access, but be careful of chmod as the inexperienced go round opening their system to the whole world.

An inadvisable option is to sudo passwd root - re-setting the root password and login as root. Hey ho. The more you know right :)

Don't want to re-login - after setting the root password just type 'su' in the command prompt and you are now elevated to root for the session and you have full power without the need to use sudo. Be your own god of your system ;).

---

### Post by jeremy31 on 2018-12-08
JayKay3OOO, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by juuchijs on 2018-12-09
Thank you all for tips and help, very valuable information for begginner. :)

---

