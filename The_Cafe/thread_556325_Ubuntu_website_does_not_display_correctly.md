---
title: "Ubuntu website does not display correctly"
date: 2007-09-21
forum: The Cafe
---

### Post by fluppet on 2007-09-21
I'm using WinXP and IE6 and the Ubuntu website does not display correctly - it looks quite unprofessional and should be fixed.

---

### Post by mindtrick on 2007-09-21
Could you provide a screenshot?

---

### Post by PartisanEntity on 2007-09-21
I just fired up ie6 in Ubuntu and I get what you mean, the borders don't align properly, was that what you meant?

---

### Post by the_darkside_986 on 2007-09-21
Why not use IE7? It looks fine in IE7 on WinXP SP2 here. Also IE7 seems to be more standards-compliant because I was trying to use some outdated html code in a project and it wouldn't display correctly in IE7 until I used CSS or something. (I can't remember what I was doing, something to do with tables I think.)

Also there are obviously security problems with IE6. My dad's PC got infected all the time until I upgraded it to SP2 and IE7 instead of 6.

---

### Post by mridkash on 2007-09-21
I knew of that problem, actually I faced it in my own website design.

But it was corrected soon. 

The problem that I figured out is with relative positioning in CSS. IE6 doesn't seem to handle relative positioning correctly.

The CSS for this website contains this code
```

#container {
[COLOR=Red]position:relative;[/COLOR]
background-color:#fff;
background-image:url(http://ubuntuforums.org/imagesorig/ub2/page-border-left-repeat.jpg);
background-repeat:repeat-y;
background-position:left;
margin:0 1%;
padding:0 0 0 14px;
}
#bg-left {
position:absolute;
top:0;
[COLOR=Red]left:0;[/COLOR]
width:14px;
height:665px;
background-image:url(http://ubuntuforums.org/imagesorig/ub2/page-border-left.jpg);
background-repeat:no-repeat;
background-position:top left;
z-index:6;
}

#bg-right {
position:absolute;
top:0;
[COLOR=Red]right:0;[/COLOR]
width:13px;
height:665px;
background-image:url(http://ubuntuforums.org/imagesorig/ub2/page-border-right.jpg);
background-repeat:no-repeat;
background-position:top right;
z-index:6;
}
```Somebody may try to solve this problem with this modified code
```
#container {
background-color:#fff;
background-image:url(http://ubuntuforums.org/imagesorig/ub2/page-border-left-repeat.jpg);
background-repeat:repeat-y;
background-position:left;
margin:0 1%;
padding:0 0 0 14px;
} 
#bg-left {
position:absolute;
top:0;
[COLOR=Red]left:1%;[/COLOR]
width:14px;
height:665px;
background-image:url(http://ubuntuforums.org/imagesorig/ub2/page-border-left.jpg);
background-repeat:no-repeat;
background-position:top left;
z-index:6;
}

#bg-right {
position:absolute;
top:0;
[COLOR=Red]right:1%;[/COLOR]
width:13px;
height:665px;
background-image:url(http://ubuntuforums.org/imagesorig/ub2/page-border-right.jpg);
background-repeat:no-repeat;
background-position:top right;
z-index:6;
} 
```Here is the original post where i posted my problem
[http://ubuntuforums.org/showthread.php?t=549000](http://ubuntuforums.org/showthread.php?t=549000)

Only if somebody can try it!

---

### Post by BigBud on 2007-09-21
Its ubuntu's way of saying "Use Firefox please"

---

