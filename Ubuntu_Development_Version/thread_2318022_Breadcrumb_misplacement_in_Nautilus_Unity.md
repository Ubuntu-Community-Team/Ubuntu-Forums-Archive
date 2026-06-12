---
title: "Breadcrumb misplacement in Nautilus Unity"
date: 2016-03-22
forum: Ubuntu Development Version
---

### Post by Joo_Alves on 2016-03-22
Hello,

I'm currently using Ubuntu 16.04 LTS (last update) and I am experiencing a visual misplacement (more specifically, between "Workspace" and "Resources") as it can bee seen in the following picture. 

[ATTACH=CONFIG]267924[/ATTACH]

Is this a normal behaviour? 

Thanks.

---

### Post by howefield on 2016-03-22
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by ajgreeny on 2016-03-22
What do you mean by "visual misplacement"?
Which folder was open in nautilus in your screenshot, Workspace or resources?
Where do you expect the breadcrumb location bar to be?

More details of the problem please, as I'm not understanding.

---

### Post by grahammechanical on 2016-03-22
I have never heard the term "breadcrumbs" used before. Except for feeding birds. I had to do a web search to get an idea what it was.

As far as I can make out you have opened nautilus and it has opened as usual in the home folder then you have opened a folder called resources. I can just about see at the right edge of the image that there is a folder highlighted and the name begins "re." But the nautilus top panel shows the resources folder as being inside the Workspace folder when it is not. Or is it? In which case I have no idea what you are referring to.

In this matter a picture has not painted a thousand words.

Or, it could be that you have only selected the resources folder and nautilus is showing it in the top panel as if it has been opened. If this is the situation what you are seeing, I guess, is nautilus showing recent history as an easy short cut for the user to go back into folders that have been recently opened. It is not a complete history of folders opened recently. Click on home and it will reset.

You opened the Workspace folder, then the resources folder and then you switched back to the Workspace folder and nautilus is still showing the resources folder in the top panel. This is what the Gnome devs want nautilus to do.

Regards

---

### Post by Joo_Alves on 2016-03-22
> **ajgreeny said:**
> What do you mean by "visual misplacement"?
Which folder was open in nautilus in your screenshot, Workspace or resources?
Where do you expect the breadcrumb location bar to be?

More details of the problem please, as I'm not understanding.

The location of the breadcrumb itself is correct. 
I'm referring to the "visual glitch" that can be seen in the screenshot. More specifically, between "workspace" and "resources" the separation between both is not being correctly displayed. 
It seems that the "resources" item has been visually unattached.

> **grahammechanical said:**
> I have never heard the term "breadcrumbs" used before. Except for feeding birds. I had to do a web search to get an idea what it was.

As far as I can make out you have opened nautilus and it has opened as usual in the home folder then you have opened a folder called resources. I can just about see at the right edge of the image that there is a folder highlighted and the name begins "re." But the nautilus top panel shows the resources folder as being inside the Workspace folder when it is not. Or is it? In which case I have no idea what you are referring to.

In this matter a picture has not painted a thousand words.

Or, it could be that you have only selected the resources folder and nautilus is showing it in the top panel as if it has been opened. If this is the situation what you are seeing, I guess, is nautilus showing recent history as an easy short cut for the user to go back into folders that have been recently opened. It is not a complete history of folders opened recently. Click on home and it will reset.

You opened the Workspace folder, then the resources folder and then you switched back to the Workspace folder and nautilus is still showing the resources folder in the top panel. This is what the Gnome devs want nautilus to do.

Regards

Breadcrumb has been a term to describe this type of navigation since long ago: [https://en.wikipedia.org/wiki/Breadcrumb_(navigation)](https://en.wikipedia.org/wiki/Breadcrumb_(navigation))
Although I also find the name interesting :P

Regarding the issue itself please see the answer provided in the previous quote response to ajgreeny

Thanks.

---

### Post by vasa1 on 2016-03-22
So you feel the space between the *workspace* and *resources* buttons is more than the space between the *home* and *workspace* button? Isn't the difference negligible?

---

### Post by vasa1 on 2016-03-22
> **grahammechanical said:**
> ... This is what the Gnome devs want nautilus to do.
...
Even PCManFM (LXDE) and Thunar (XFCE) have something similar.

---

### Post by Joo_Alves on 2016-03-22
> **vasa1 said:**
> So you feel the space between the *workspace* and *resources* buttons is more than the space between the *home* and *workspace* button? Isn't the difference negligible?

[ATTACH=CONFIG]267926[/ATTACH]

I believe this to be a better image of the situation. It seems that the rendering is wrongfully ending the breadcrumb while it still has more items.
This happens when I select an item that is not the last. All the remaining items, more specifically their separation, look weird.

Thanks

---

### Post by Joo_Alves on 2016-03-22
And sometimes it works correctly:

[ATTACH=CONFIG]267927[/ATTACH]

---

### Post by vasa1 on 2016-03-22
Which theme are you using? Can you try a theme other than Ambiance/Radiance?

---

### Post by Joo_Alves on 2016-03-22
> **vasa1 said:**
> Which theme are you using? Can you try a theme other than Ambiance/Radiance?

Can you recommend me one? I've tested with "high-contrast" and the issue still happens.

---

### Post by mc4man on 2016-03-22
Don't see what the issue is. It appears you've opened 1 folder past, then gone back. The folder you are in will have it's breadcrumb highlighted with a slight radius on it's trailing corners.

---

### Post by Joo_Alves on 2016-03-22
> **mc4man said:**
> Don't see what the issue is. It appears you've opened 1 folder past, then gone back. The folder you are in will have it's breadcrumb highlighted with a slight radius on it's trailing corners.

The issue is the inconsistency of the rendering:

[ATTACH=CONFIG]267929[/ATTACH]    [ATTACH=CONFIG]267930[/ATTACH]

In the first image you can see that the item borders are being incorrectly displayed while in the second image everything is fine.

Also, sometimes even with the last item selected the problem occurs in the previous items.

---

### Post by mc4man on 2016-03-22
Well I was in one of these 'no menus' logins which seemed to have inconsistent results with multiple breadcrumbs. Now back in a 'normal' session I see with ambiance something similar to what you see except if focus is removed from nautilus, then returned. After that  the radius is only at the front & back of the group if in the last crumb folder or at the back of the folder in if not in the last folder.

So there is a minor little bug there, myself wouldn't change a theme over..

screen 1 shows 'proper' behavior after removing then returning focus
screen 2 shows improper behavior

---

### Post by Joo_Alves on 2016-03-22
> **mc4man said:**
> Well I was in one of these 'no menus' logins which seemed to have inconsistent results with multiple breadcrumbs. Now back in a 'normal' session I see with ambiance something similar to what you see except if focus is removed from nautilus, then returned. After that  the radius is only at the front & back of the group if in the last crumb folder or at the back of the folder in if not in the last folder.

So there is a minor little bug there, myself wouldn't change a theme over..

screen 1 shows 'proper' behavior after removing then returning focus
screen 2 shows improper behavior

I agree, i just felt it would be better to report the issue. I'm not sure if this is the best place to do it though, so if not please advise me.

Thanks.

---

### Post by mc4man on 2016-03-22
> **Joo_Alves said:**
> I agree, i just felt it would be better to report the issue. I'm not sure if this is the best place to do it though, so if not please advise me.

Thanks.
You would want to file a bug, probably against light-themes as in from a terminal
```
ubuntu-bug light-themes
```

To actually file you'll need to login, to do that you need a Lauchpad account, see here
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

You'd want to describe clearly & list steps on how to reproduce. Also in this case attach a screenshot or 2 that shows issue

---

### Post by ajgreeny on 2016-03-22
> **mc4man said:**
> Well I was in one of these 'no menus' logins which seemed to have inconsistent results with multiple breadcrumbs. Now back in a 'normal' session I see with ambiance something similar to what you see except if focus is removed from nautilus, then returned. After that  the radius is only at the front & back of the group if in the last crumb folder or at the back of the folder in if not in the last folder.

So there is a minor little bug there, myself wouldn't change a theme over..

screen 1 shows 'proper' behavior after removing then returning focus
screen 2 shows improper behavior
I wonder if this is a rendering problem related to the graphic card in use, because as I switch from your screen-1 to screen-2, as far as I can see they are identical right down to the last pixel; I was expecting to see a very small change as I swapped from image to image, but nothing at all shows, not even a flicker.

---

### Post by mc4man on 2016-03-22
> **ajgreeny said:**
> I wonder if this is a rendering problem related to the graphic card in use, because as I switch from your screen-1 to screen-2, as far as I can see they are identical right down to the last pixel; I was expecting to see a very small change as I swapped from image to image, but nothing at all shows, not even a flicker.

Try looking at again, am curious - 
In screen 1 there are 4 crumbs, there is only a radius on left of 1st crumb & right of last crumb, otherwise all straight lines between crumbs
In screen 2 there are same 4 crumbs, crumb's #2 & #3  have radius on their right sides, folder that is open on end has no radius on right side

---

### Post by Joo_Alves on 2016-03-22
> **mc4man said:**
> You would want to file a bug, probably against light-themes as in from a terminal
```
ubuntu-bug light-themes
```

To actually file you'll need to login, to do that you need a Lauchpad account, see here
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

You'd want to describe clearly & list steps on how to reproduce. Also in this case attach a screenshot or 2 that shows issue

Ok thank you. I will follow the report steps.

---

### Post by ajgreeny on 2016-03-22
> **mc4man said:**
> Try looking at again, am curious - 
In screen 1 there are 4 crumbs, there is only a radius on left of 1st crumb & right of last crumb, otherwise all straight lines between crumbs
In screen 2 there are same 4 crumbs, crumb's #2 & #3  have radius on their right sides, folder that is open on end has no radius on right side
Sorry, but try as I might, I can still see no difference at all between the two screenshots, and I have looked as carefully as it is possible to do, going from #1 to #2 and back again in quick succession.

---

### Post by Joo_Alves on 2016-03-22
> **ajgreeny said:**
> Sorry, but try as I might, I can still see no difference at all between the two screenshots, and I have looked as carefully as it is possible to do, going from #1 to #2 and back again in quick succession.

Please refer to the following picture which clearly represents the issue:

[ATTACH=CONFIG]267941[/ATTACH]

---

### Post by vasa1 on 2016-03-22
> **ajgreeny said:**
> ..., going from #1 to #2 and back again in quick succession.
Sheldon did something like that in one TBBT episode:> The episode begins with Sheldon trying to engage his superior-colliculus by quickly whipping his head back and forth at a whiteboard full of equations to create a fleeting peripheral image.Source: [some wiki about Season 3 Episode 14]("http://bigbangtheory.wikia.com/wiki/The_Einstein_Approximation")
After a while, he threw the whiteboard "out the window".

---

### Post by Joo_Alves on 2016-03-23
I've noticed that the issue doesn't appear when I'm on Gnome with Adwaita theme:

[ATTACH=CONFIG]267948[/ATTACH]

---

### Post by ajgreeny on 2016-03-23
> **Joo_Alves said:**
> I've noticed that the issue doesn't appear when I'm on Gnome with Adwaita theme:

[ATTACH=CONFIG]267948[/ATTACH]
I've never used gnome since Ubuntu 10.04 with gnome 2.  Is the gnome 3 version using a 3d desktop, and if not could that be the problem you are seeing in unity?

---

### Post by motang on 2016-03-24
I get that too, but it seems to be that after you take the window out of focus and put it back into focus it is fixed.

---

