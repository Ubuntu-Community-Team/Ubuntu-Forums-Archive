---
title: "Minimizing Terminal or Shell Usage (Minimizing Typing)"
date: 2008-11-27
forum: Ubuntu Brainstorm
---

### Post by digitalbrain on 2008-11-27
Hi. I have a simple idea. Maybe this was discussed in a thread before but I couldn't find it. I will try to explain it with an example. 
In order to copy (or cut) a file from a user owned folder (e.g. /home/user) and paste it into a root owned folder (e.g. /bin), we are using terminal. That means typing a lot of things such as   ```
 sudo cd /home/user/bla/bla   sudo cp /bla  bla/bla/bla 
``` and then we are asked for password. Instead of typing many things, when I open that user folder and right-click the file (or files) I should choose "copy" from the menu  and then right-click /bin folder which I want the file to be copied into, then select "paste" (but there is no "paste" option there) and exactly at that moment I should be asked for my password. And after writing my password, the paste process should be done. According to me it is a waste of time using the terminal for doing this. I should simply copy-paste the files with mouse clicks (or by dropping and dragging) . And at the end of that last click, I should be asked for my password within a box just like I am asked when using synaptic or update manager. Also when creating a shortcut of a root program on desktop, we can do it in this way again. Simply right-click, "create shortcut", write password. These are just simple examples. That can be done in many other things. The idea is to minimize the usage of terminal (without breaking down security of course) and to use the computer much more easily for certain things. I find typing commands and using terminal every time very boring indeed. I hope I could have been clear. 
Can that be done? Thanks.

---

### Post by Idefix82 on 2008-11-27
Firstly, you can just start your file browser with root privileges by
```
gksudo nautilus
```
and after typing in your password once you can do all the copying and pasting you like without being asked for a password again. Beware that you will need to browser to your home folder by hand since 'Home' will now refer to the superuser's home folder.

Secondly, in my opinion it is a complete waste of time to work with the mouse when you can do it in the terminal, because the latter is much faster. You do know about tab completion, do you? You start typing a directory name and hit tab. It either autocompletes or notifies you of the fact that you haven't typed enough to identify the directory uniquely. You hit tab again and you see all the options of continuing your command. Of course I am still assuming reasonable typing skills.

---

### Post by digitalbrain on 2008-11-27
> **Idefix82 said:**
> Firstly, you can just start your file browser with root privileges by
```
gksudo nautilus
```
I don't mean having root privileges completely. That's not what I want. I want to do certain things with mouse (or keyboard shortcuts) instead of typing commands in terminal or let's say, doing them without using terminal at all.

---

### Post by tiachopvutru on 2008-11-29
Well, there's an option available in Ubuntu similar to what you are suggesting if you install **nautilus-gksu** package in Synaptic. After that, you can right-click and open a folder as administrator.

I do believe your idea is better, though.

However, even in terminal, it doesn't take that much typing. Just drag the file you want to copy and the folder destination into terminal. It will automatically give you the paths.

---

### Post by 3rdalbum on 2008-12-02
The idea has been around for many years. I have no idea why it has never been implemented; it's more intuitive than the current method and is more secure (only the file-copying code runs as root, rather than an entire file manager).

---

