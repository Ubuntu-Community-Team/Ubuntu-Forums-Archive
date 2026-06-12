---
title: "How to Setup a Truly Seamless Virtual Machine"
date: 2011-10-13
forum: Tutorials
---

### Post by hwttdz on 2011-10-13
So I don't use windows frequently (ever), but I do interact with people who do occasionally, many of whom frequently ask for help with their broken machine.  And as much as we sometimes get frustrated with linux, I need only try to use windows and notice, "what do you mean I can't set which program opens when I right click 'edit' a file?" before I'm wishing to go back.  But anyways, people who like to keep windows around as a crutch will do so.  Splicing a few different ideas together, namely multiple backgrounds on multiple desktops and some xdotool keyboard automation and I've got a nice little workspace manager which:

1) changes the wallpaper according to the workspace you're currently on which gets you 
    a) desktop icons and
    b) per workspace wallpapers (I haven't seen a good solution to get both of these at the same time)
    c) in either metacity or compiz (known compiz bug, only supports 1 row of workspaces)

2) a workspace which is running windows, and yet doesn't consume any resources when you're not on the windows workspace.

How this works:
It's in an infinite loop checking what workspace you're currently on and keeping track of the last one as well.  If the workspace changes it changes the desktop wallpaper.  If you happen to change to the windows workspace it starts the windows virtual machine in fullscreen mode.  But as I don't like dealing with the host key nonsense I use the workspace watcher to get me out of windows when I need to as well.  Namely, I put a .bat on my desktop which creates a file in a folder shared between the host and the guest os.  If the watcher sees that file exists, it quits the virtual machine (saving it's state) and changes to another workspace.  The time to resume the virtual machine from a saved state and suspend to said saved state again is on the order of seconds.  

So what the user sees, 
1) ability to changes workspaces however you want (mouse, keyboard)
2) different wallpaper on each workspace, with desktop icons
3) one workspace is running windows and to exit the windows workspace you have to run a batch script on the desktop.

The original (without VM support) is described and linked to from [here]("http://astoryworthtelling.wordpress.com/2011/10/12/one-wallpaperbackground-per-desktopworkspace-in-ubuntu-with-icons/") and the new version with VM support is [here]("http://www.columbia.edu/~jhb2147/vm_desktop_watcher.pl").

Obviously you'll have to adjust the virtual machine name and which flag file it checks for.  The bat file is as simple as 
"echo hello world > Z:\flag_file" (if I wanted to check for flag file on drive Z (which probably maps to a folder on the linux side).

---

