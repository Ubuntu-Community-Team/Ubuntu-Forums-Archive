---
title: "Suggestions for organizing directories please"
date: 2005-03-21
forum: The Cafe
---

### Post by Taoism on 2005-03-21
Hi all,

I'm a Linux n00b, so be gentle  ;-) 

I downloaded a third-party program last night (EditPadPro), and it is running from a downloads directory I created in my main (not root) user account.

If I wanted to make it so that anyone on the box could run that program, where would I want to move it to (i.e. is there a standard directory/subdirectory where an administrator would put applications they install after the system is up and running)?

Would I need to make Gnome aware of the application somehow to get it into the menu system for Gnome?

Also, if anyone has recommendations for a good editor (not vi please :) ).  I am used to using, UltraEdit, PHPEdit, and occassionally Eclipse in the Windows environment for my development.  I am trying EditPadPro since it seems like it is a little closer to UltraEdit than anything else I have run across on Linux so far.

Any help/suggestions would be appreciated!

Cheers,
Keith.

---

### Post by jnoreiko on 2005-03-21
[QUOTE=Taoism]Also, if anyone has recommendations for a good editor (not vi please :) ).  I am used to using, UltraEdit, PHPEdit, and occassionally Eclipse in the Windows environment for my development. [/QUOTE]

I recommend NEdit. It has powerful features, excellent syntax highlighting, and has all the GUIO features you'd expect.

As far as your application problem goes... I'm a n00b too  :)  so I'm not sure... I think you're supposed to use the package management tools like apt-get to install stuff rather than just unzip and run it.

---

### Post by bored2k on 2005-03-21
[QUOTE=Taoism]Hi all,
If I wanted to make it so that anyone on the box could run that program, where would I want to move it to (i.e. is there a standard directory/subdirectory where an administrator would put applications they install after the system is up and running)?

Also, if anyone has recommendations for a good editor (not vi please :) ).  I am used to using, UltraEdit, PHPEdit, and occassionally Eclipse in the Windows environment for my development.  I am trying EditPadPro since it seems like it is a little closer to UltraEdit than anything else I have run across on Linux so far.

[/QUOTE]

You have to change permissions on the file. Right click on the dir and checkmark on read/write/execute on all. Or in a terminal hit
chmod 777 /home/user/application [GUI is easier].

Editor -> Anjuta IDE is the most complete solution I have seen this side of earth.

---

