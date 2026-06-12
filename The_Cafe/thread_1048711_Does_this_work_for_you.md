---
title: "Does this work for you?"
date: 2009-01-23
forum: The Cafe
---

### Post by linuxisevolution on 2009-01-23
I am working on a web site for Linux. I seem to have it almost finished, but the page never completely loads... Does it work for you?

[http://www.linuxforums.tk/]("http://www.linuxforums.tk/")

EDIT: I think I fixed it. Before all I saw was:

<div id="preload" style="display: none;">
<img src="load.gif">
Loading... Watch the circle. 
</div>
<script type="text/javascript">
// preloader
document.write('<div id="preloader" style="height: 100%;width: 100%;text-align: center;position: absolute;top: 0;z-index: 9000;"><span style="margin: 0 auto;">'+document.getElementById('preload').innerHTML+'</span></div>');
window.onload = function() {document.getElementById('preloader').style.display = 'none';}
</script>


It showed a spinning circle and said "watch the circle" LOL. Coding has it's humor ;)

---

### Post by Sealbhach on 2009-01-23
Took a few seconds to load, but it works. It's little screenshots revolving, and they follow the cursor.  I clicked on one but it doesn't open.

Is that right? I'm using Firefox 3.2a1pre.


EDIT: 2nd time i tried I got gray vetical bars spinning around. Took about 12 seconds to load.

.

---

### Post by gettinoriginal on 2009-01-23
1 min 50 sec to get all 5 of the rotating screens, but looked like this
[ATTACH]100869[/ATTACH]

---

### Post by linuxisevolution on 2009-01-25
Thanks everyone. I realized now that the IP to my server changed and the link to the images in the XML code was a bit flakey so the images could not load correctly. I set my network to static so it won't happen again. Now I just have to revert the code in the applet. :popcorn:

---

