---
title: "Need some help with editing signature, please..."
date: 2014-10-10
forum: Resolution Centre
---

### Post by Mike_Walsh on 2014-10-10
Good afternoon.

I appear to have a problem with trying to edit my signature. I was attempting to add my reistered Linux user number to it; I know the character limit is 500. I WAS up to about 350; I've had to delete about half of my original signature, but it keeps insisting my 'BB code size value' is too big. Is it possible to reset this, or alter it, please.....and if so, can I do this myself, or can it only be changed by staff?

Any advice or help would be very much appreciated. Thank you.

Regards,

Mike.

---

### Post by coffeecat on 2014-10-10
Were you trying to set BBCode [noparse][SIZE=2][/SIZE][/noparse] or greater using BBCode? I've found this setting for your usergroup: Maximum Value of x for [SIZE=x] BB Code = 1. Which is a bit weird - par for the course for vbulletin though. BBCode size 1 is smaller than the default. Default is size 2, and sizes 3 to 7 are large ranging to giant. What this seems to mean is that if you don't use BBCode size tags you get default size 2, but that you are allowed small size only if you do use BBCode size tags. When I say seems to mean is that these settings were made years ago, and I guess it was to prevent people from creating sigs with crazily large letters. 

The other settings which might help you compose your sig are:

Maximum Characters in Signature Including BB Code Markup = 500
Maximum Characters in Signature Excluding BB Code Markup = 250.

Which I take to mean up to 250 characters of ordinary text and up to 250 characters of BBCode.

---

### Post by Mike_Walsh on 2014-10-10
Hi, coffeecat.

Thanks for looking into it for me. Do I take it that a certain amount of user alteration is permitted with the BBcode? I'll be honest, I'm not even sure what BBcode is ('b'ulletin 'b'oard?) I mean, you can see my sig for yourself; quite short and neat, and I simply want to add 'Registered Linux User #******' to it; I wouldn't have thought that would have pushed it over the combined limit (?) I don't know; I'm not even sure what part the code plays in the overall length of the signature..!

Regards,

Mike.

---

### Post by coffeecat on 2014-10-10
BBCode is things like [noparse]```

```> ****[/noparse], and so on. You can only use the BBCode that is defined for this forum. We use a large subset, but not the full Monty:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)

Here's the BBCode in your current sig without the text and carriage returns:

[noparse][FONT=arial]*[COLOR=#000000][/COLOR][COLOR=#cc3300][/COLOR][COLOR=#0000ff][/COLOR][COLOR=#800080][/COLOR][COLOR=#6666cc][/COLOR]****[COLOR=#ff0000][/COLOR]*****[/FONT]

That's a lot of BBCode - 178 characters, below the 250 limit, but still a lot.

You didn't answer my question whether you were using the [size=x][/size] tags. Why don't you post the whole of what you are trying to use as a sig and which is giving you an error, and perhaps we can see what is causing the problem? If you do, bracket the whole of the sig text between {noparse} and {/noparse} BBCode tags otherwise the forum software will parse the BBCode.[/noparse]

By the way, noparse tags have square brackets. I had to use curly brackets as illustration because there are already a load of (invisible) noparse tags in my post and the forum software got confused when I tried to use square bracket noparse tags as text as well as tags.

---

### Post by coffeecat on 2014-10-10
I&#8217;ve just realised I can test the error message you mentioned in your first post. Admins have the same restriction, in effect, to other usergroups with regard to BBCode text size in sigs. Trying to insert text with [noparse][size=3]test[/size][/noparse], I see:

> BB code size value is too big. 


You were indeed trying to use the [noparse][size=x][/size][/noparse] tags. The only value you can use is 1 for small text. No large text allowed. That&#8217;s where you were going wrong. See my comments in post #2.

---

### Post by Mike_Walsh on 2014-10-10
Hi again, coffeecat.

Hm. So the font size, colour, and so on, ALL generates BBcode tags? I can see what my biggest user is, in that case; my multi-coloured distro labels (orange for Ubuntu,Dark blue for Zorin, light blue for Kubuntu, etc.).....they're generating one **&#8203;hell **

---

### Post by Mike_Walsh on 2014-10-10
Sorry for that last post, coffeecat.....hit the send button too soon. Of course, you can't edit anything in this section, can you?

I was going to say, I think my multi-coloured distro labels look to be the biggest culprit, wouldn't you say? Every time I deviate from standard black, it generates another 10-12 characters of code, doesn't it? (Thanks for showing it to me like that; makes it all TOO clear *sigh*)

Anyway; I'm going to say thanks VERY much for the help on this. I can see what you mean by the BBcode, now; amazing how just a few seemingly simple changes can generate all that extra guff... Wouldn't have believed it if I hadn't seen it with my own eyes!

Yet ANOTHER little tip I've learnt today; it's not only a steep, but sometimes quite a fast learning curve in not only Linux, but the forums, too...

Much appreciated.

Regards,

Mike.

---

### Post by Elfy on 2014-10-10
Try not using Size tags.

---

### Post by Mike_Walsh on 2014-10-10
Hi again.

[I][COLOR=#000000][noparse]Distros: [/COLOR][COLOR=#cc3300]Ubuntu 14.04 LTS,[/COLOR] [COLOR=#0000ff]Zorin OS Core 9, [/COLOR][COLOR=#800080]&#8203;Lubuntu 14.04, [/COLOR][COLOR=#6666cc]Kubuntu 14.04[/COLOR]
Athlon64 3200+, 3GB RAM, 160GB Caviar 'Black', ATI graphics.
[B]
Don't forget..... [/B][COLOR=#ff0000]&#8203;Back your data up, [/COLOR]**before** making major changes! Registered Linux User #579645[/noparse][/I]

That's what I was trying to achieve. But if changing things back to black, without bold accentuation, etc., will make it work better, that is what I shall have to do..!

Regards,

Mike.

BTW, I did try going down to size 1, briefly, before I found out that wasn't the problem (at least, that was what I thought at the time...) :confused:

---

### Post by Mike_Walsh on 2014-10-10
> **Elfy said:**
> Try not using Size tags.

Hi, Elfy.

I think I'm making TOO many variations in a very short length of text, aren't I?

These code tags are taking a bit of getting used to... (lol)

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-10
Hi, all.

SORTED.  I
               I
               I
           \   I   /
            \  I  /
             \ I /
              \I/
               I

THAT'S what I was after.

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-10
My arrow didn't turn out too well, did it?

Anyway; 'Solved'.

Thanks, guys!

Regards.

Mike.

---

### Post by Elfy on 2014-10-10
Try without the empty line - I've tried your exact sig with another user. Works fine without the line between.

---

### Post by Mike_Walsh on 2014-10-10
Cheers for that, Elfy; I'll give it a try in a few.

SMOKE time! :D

Regards, Mike.

---

