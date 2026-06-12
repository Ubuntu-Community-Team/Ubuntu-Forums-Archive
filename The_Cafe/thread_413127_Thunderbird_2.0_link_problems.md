---
title: "Thunderbird 2.0 link problems"
date: 2007-04-18
forum: The Cafe
---

### Post by FreakTech on 2007-04-18
I have no idea where to post this.  I have already been all over the Mozilla forums and no one seems to be using linux.

I am using Thunderbird 2.0, and none of my links work.  Not in emails or in the menus such as the add on box where you click to get themes or extensions.  Has anyone else had this problem?  Any ideas on how to fix it.  

Thanks in advance for any help.

---

### Post by odzx on 2007-04-21
same problem here

---

### Post by Ender Black on 2007-04-21
That's a strange one.  My TB 2.0 links are working as intended.  The only thing that I found that would allow me to screw with it was View -> Message Body -> Original HTML.  I guess you could check that.

---

### Post by odzx on 2007-04-21
looking around actually shows this problem to a common one in previous versions and there are some fixes like this one here [http://ubuntuforums.org/showthread.php?t=60427&page=3]("http://ubuntuforums.org/showthread.php?t=60427&page=3")
and here [http://ubuntuforums.org/showthread.php?t=60427]("http://ubuntuforums.org/showthread.php?t=60427")
but they did not work for me on this version.

---

### Post by odzx on 2007-04-21
finally this worked for me:
opened 'all.js' file with a text editor (for me it was in:  /home/oded/thunderbird/greprefs) and added this three lines at the bottom:
> pref("network.protocol-handler.app.https","/usr/bin/firefox");
pref("network.protocol-handler.app.http","/usr/binl/firefox");
pref("network.protocol-handler.app.ftp","/usr/bin/firefox");
i don't know if that's the way it should be done but it's the the only way it worked for me.

---

