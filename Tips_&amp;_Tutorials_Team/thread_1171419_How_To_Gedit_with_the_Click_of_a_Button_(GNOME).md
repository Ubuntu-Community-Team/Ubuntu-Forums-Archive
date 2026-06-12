---
title: "How To: Gedit with the Click of a Button (GNOME)"
date: 2009-05-26
forum: Tips &amp; Tutorials Team
---

### Post by BslBryan on 2009-05-26
Hello, everyone. :-)

Have you ever found yourself dealing with editing several files, and sighing at having to type out different "gedit" commands in the terminal?  

**If I correctly described an experience that you've had, the following tutorial is a must.**  [COLOR="Red"]My tutorial allows you to add "Open with gedit" to the Right-click menu, making it easy to gedit anything![/COLOR] :-)

First, we need to run this command in the terminal, making the file that will hold our script:
```
gedit ~/.gnome2/nautilus-scripts/Open\ with\ gedit
```

Now, a blank document in the text editor should open.  Copy and paste these contents:
```

#!/bin/bash
#
# Nautilus script -> open gedit
#
filesall=""
while [ $# -gt 0 ]
do
files=`echo "$1&#8243; | sed 's/ /\?/g'`
filesall="$files $filesall"
shift
done
gedit $filesall&
```

Now click save, and close the text editor.  

Finally, we need to make the previous script executable.  So let's run this command:
```
chmod u+x ~/.gnome2/nautilus-scripts/Open\ with\ gedit
```

And that's it!  Open up the file browser, and right-click on any file to test it out!

I hope I've helped to make someone's life a lot easier.  Enjoy, everyone.

---

### Post by frodon on 2009-05-27
Isn't it way easier and more supported to use nautilus-action ?
[http://ubuntuforums.org/showthread.php?t=91377](http://ubuntuforums.org/showthread.php?t=91377)

I find this guide redundant and a bit using the old way of doing things, opinions ?

---

### Post by bodhi.zazen on 2009-05-27
> **frodon said:**
> Isn't it way easier and more supported to use nautilus-action ?
[http://ubuntuforums.org/showthread.php?t=91377](http://ubuntuforums.org/showthread.php?t=91377)

I find this guide redundant and a bit using the old way of doing things, opinions ?

+1

This is a user script and not a tutorial.

Not to discourage BslBryan , but IMO it belongs on a blog not the T&T section.

---

### Post by frodon on 2009-05-28
Ok i will delete it and propose the user a copy of his thread if he want one.

I think a nautilus-action up to date and complete tutorial would be great, so i will talk to him about it, just in case he's interested creating one.

---

