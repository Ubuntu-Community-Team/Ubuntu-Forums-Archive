---
title: "Password Prompt for Moving Files"
date: 2008-09-15
forum: Ubuntu Brainstorm
---

### Post by Mad_Max_1412 on 2008-09-15
Hi Guys,

I'm a relatively new user and would like to offer a suggestion on a future feature that might make things a little easier for users.

In case you need the info as background, my Ubuntu box automatically logs into only one account.

Anyway, the other day I downloaded a file, a torrent, and it saved to the desktop.  I then went to move it to a folder I created and it said I didn't have permissions.

A quick search of the forums showed I needed to run a "gksudo nautilus" command so that I had permission.  I also found out that some people create a shortcut to this command, which I've also done.

My suggestion is that perhaps if someone goes to move a file and doesn't have permission, then perhaps it should offer the chance to input the Admin password, the same as what happens when you try to check/install updates.

BTW, I don't understand why, when I start Ubuntu and it automatically logs in and I used this logged in session to download a file, why I don't have permission over that downloaded file??  I guess that's a whole new discussion, but the point here was to suggest the password prompt idea rather than having newbies (or even experienced) people having to re-open a file management app with the appropriate permissions.

Thanks

---

### Post by smartboyathome on 2008-09-16
That is a bug. You must have accidentally redone your permissions. Try chown username:username * in your home directory, replacing username:username by your username on your computer.

About the suggestion: I think it would be more of a flaw, due to people dragging files to their system folder and breaking stuff. I think if this could be limited to the /home folder, it would be fine, but outside of that I don't like the idea.

---

### Post by cdenley on 2008-09-16
I'm not sure why you're having permissions issues for that directory. If you are interested in determining the cause of the problem, you would need to provide more details such as "ls -l /path/to/my_downloaded_file" and "ls -ld /path/to/my_dest_dir".

As far as your idea, I agree with smartboyathome that it wouldn't be a good idea. They don't have access to system directories for a reason. There shouldn't be a typical desktop user function that requires nautilus to be run as root. I've never run nautilus as root. I can't imagine why people are suggesting creating a launcher for "gksudo nautilus". Of course, having the option available but disabled by default wouldn't be so bad.

---

### Post by Mad_Max_1412 on 2008-10-02
Hi cdenley,

I figured out why I couldn't move my files into the directory.

I have a WinXP computer which has a drive mapped to one of my Ubuntu directories where I keep some files.  Whilst on the WinXP computer, I created a sub-folder in this Ubuntu directory.

When I look at this sub-folder in Ubuntu, it has a padlock symbol.  I can't drag any files into it.

If I create the sub-directory whilst on the Ubuntu box, then I can drop files into it.

Quick question regarding the sub-directories I've created via WinXP's mapped drive - How can I get permission to use it?  Under the permissions tab, the owner is "Nobody" and the other options are greyed out.

I guess the easiest method is just to create a new folder whilst in Ubuntu (so I have permission to it) and then use the "gksudo nautilus" command to move files out of these "locked" directories and delete them once empty.

PS - sorry for taking so long to get back to you, as I've been very busy lately and haven't had time to investigate anything.

---

