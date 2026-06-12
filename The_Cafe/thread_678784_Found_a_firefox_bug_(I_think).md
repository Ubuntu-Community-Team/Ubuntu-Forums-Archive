---
title: "Found a firefox bug (I think)"
date: 2008-01-26
forum: The Cafe
---

### Post by mr.propre on 2008-01-26
I'm posting it here because I'm not really a firefox user, but I know that allot people are using FF and hoping to find answers here.

I just made a little flash animation to put into my website, because I'm still a fan of valid code (I find it cool) I changed the object code and removed the embed tag because this is not valid.

After successful testing in Opera and IE, I tested in Firefox, with a failed test as result. For some reason FF need the embed tag. 
Is this a bug, and is this know by mozzilla, because I know that Mozzilla prefers to make there browsers xhtml valid.

Thanks in advance.

---

### Post by Abild on 2008-01-26
It should be possible to embed a flash movie in mozilla browsers using only standards-compliant markup. Have a look at [this]("http://www.alistapart.com/stories/flashsatay/") and see if it works out for you.

---

### Post by mr.propre on 2008-01-26
I have based my code on that article, maybe I just made a typo, will try it again :confused:

---

### Post by theonhighgod on 2008-01-26
this is a commonly reported problem, the code ive taken to using is this:

```
<object
type="application/x-shockwave-flash" data="linkto.swf" 
width="157" height="107">
<param name="movie" value="linkto.swf" />
</object>
```

it seems to work in all the browsers, its technically nearly totally valid, only problem is in Firefox it doesn't seem to cache or partially load the swf, in stead it downloads the whole thing then open it, less then ideal, but at least its fairly succinct and valid, for more details see this link:

[http://www.w3schools.com/flash/flash_inhtml.asp](http://www.w3schools.com/flash/flash_inhtml.asp)

---

### Post by mcduck on 2008-01-26
I always use following code to add flash to websites. It's valid XHTML 1.0 and works in every browser I've tried:

```

<object	type="application/x-shockwave-flash"
	data="base-video.swf"
	width="432"
	height="307"
	>
	<param name="allowScriptAccess" value="sameDomain" />
	<param name="movie" value="base-video.swf" />
	<param name="quality" value="high" />
	<param name="bgcolor" value="#24160d" />
</object>

```

---

### Post by mr.propre on 2008-01-27
I followed mcduck advice and it seems to work.
Thanks for the help.

---

