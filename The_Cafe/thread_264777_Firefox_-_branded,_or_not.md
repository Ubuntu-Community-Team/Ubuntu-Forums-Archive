---
title: "Firefox - branded, or not?"
date: 2006-09-25
forum: The Cafe
---

### Post by kripkenstein on 2006-09-25
Following discussion [here]("http://www.ubuntuforums.org/showthread.php?t=263367") and elsewhere, I thought a poll might be interesting.

For details, see the link given above. But, to summarize briefly: Mozilla will let distros use the Firefox code freely. However, if a distro wants to actually call it 'Firefox' and use the offical artwork/logos, the distro must either (1) not change the Mozilla code at all, or (2) get permission for all changes from Mozilla (before making each one of those changes). Thus, the Firefox code is free, but the artwork is not; also, the 'Firefox' trademark may only be used alongside the official branding, artwork, logo, etc. I hope I am summarizing this correctly.

Currently Debian is debating what to do regarding this. Ubuntu also has a problem here, seeing as Ubuntu ships a modified version of Firefox; however, Ubuntu is not limited to the Debian Free Software Guidelines, and can make its own choice here. The options Ubuntu has (unless Mozilla change their mind, which seems doubtful at present) are:

1) Distribute Firefox unchanged, exactly as it comes from Mozilla. This means no more disabling of updates inside Firefox, and other things.

2) Continue to modify Firefox, but call it by another name, and not use the original artwork/logo.

3) Include both versions, somehow. Obviously there are many ways to do this; here is one: either Epiphany or a modified Firefox - called something other than 'Firefox', of course - is installed by default. However, a simple apt-get install Firefox retrieves a completely unchanged version of Firefox.


Please note that the question put forth in this poll is **not** related to the issue of whether Firefox should be the default browser in Ubuntu. Even should Ubuntu move to Epiphany or something else, Firefox would still be in the repos; the question is, how: branded, or not?

---

### Post by v8YKxgHe on 2006-09-25
I say distribute an unchanged one. Why do we need a changed one anyway? What do they actaully do to it, apart from disable updates - but why would they even want to disable those?

---

### Post by muep on 2006-09-25
The modifications are made for a purpose. though I don't know much more about it. I think the ability to improve and fix the browser is more important than having the official artwork. Or even the name.

Fork it! :)

---

### Post by muep on 2006-09-25
AlexC_:

For example, at least in Ubuntu 4.10 and 5.04 they backported a lot of Firefox security fixes to an older version, because the new version would have broken some other packages. The ability to do this is important, I think. It is also good to be able to do some other, perhaps integration related stuff to the browser, if there is a need.

Using the Firefox auto-updates is highly advised against. It bypasses the package management system that should be aware of all the installed stuff.

---

### Post by Luggy on 2006-09-25
Ubuntu is Free and will always be Free.
If the Firefox logo and name is not Free then Ubuntu should not use it because of principal alone.

Firefox is dead, long live IceWeasel!

---

### Post by zachtib on 2006-09-25
i think the community needs to get together and demand that mozilla allows the use of the firefox name and icon regardless.

while i understand there are some problems with this, mozilla should at least make exceptions for certain projects, such as ubuntu, which modifies the code only (AFAIK) to remove the auto update function, which is handled by the package manager (IMO, no linux app should ever need or include an auto-update feature)

---

### Post by Virogenesis on 2006-09-25
Use Epiphany and modify that and add firefox to the repos, if so unhappy with  the icon, remember that the ubuntu icon itself is copyrighted.
If debian want to bitch about using the Firefox name then they should be using Epiphany.
Fact is Firefox is free so they don't want to get a bad name, Epiphany runs faster. 
Using Firefox, changing the name and icon will confuse users, it will also **BREAK** compatiablity with Firefox itself I'm guessing.
I know for a start both debian and ubuntu would be bitching if someone used their names or logo.
Firefox was designed for the FOSS market not FLOSS.
Seeing the FLOSS community have a go at Mozilla its quite sad, considering what work has been done.

---

### Post by Rhapsody on 2006-09-25
Well I like my Firefox to be Firefox, so I use the official Mozilla binaries anyway. I'm on Kubuntu, so I don't worry too much about what Ubuntu comes packaged with.

I actually lay in bed last night trying to thing up of solutions like this, and I eventually came to a conclusion.

Going to extremes with the trademarks either conservative (like what they're doing now) or liberal (GFDL or similar) is easy, and both have upsides and downsides. The tricky thing is finding a consistant middle. If you allow the logo only for non-commercial usage and Ubuntu includes it, then Ubuntu can't be sold and you have a clear violation of the GPL. If you allow commercial usage, people other than the Mozilla Corporation could start making money off their brand, which is clearly what they're unhappy about.

I'd still like to see the Firefox name and logo available under less restrictive terms, but I'm more happy to leave things as they are after thinking about the complexity of it all.

---

### Post by kigina on 2006-09-25
> **Luggy said:**
> Ubuntu is Free and will always be Free.
If the Firefox logo and name is not Free then Ubuntu should not use it because of principal alone.

Firefox is dead, long live IceWeasel!

no its not dead, you just don't use it.

---

### Post by Jucato on 2006-09-25
We have a very interesting (and unfortunate) situation here:

Debian cannot include the Firefox logo, because its license conflicts with the DFSG. So they have to modify the defaults and use a different logo. But they still use the name of Firefox. I'm not familiar with the whole process, but even if Debian submits patches upstream to Firefox, it still ships Debian's own version of Firefox, with or without MozCo's approval.

Looking at it from MozCo's point of view, they have to protect their name, too. Debian's own name and logo are also trademarked (just like Ubuntu's). While users are free to change icons to their own liking, distributors don't have exactly the same freedom. They're responsible both to their users and their upstream source. And as for patches, we can't blame MozCo for trying to preserve the integrity of their name and reputation. Imagine if some patch of Debian went wrong? Users might unknowingly blame Firefox/MozCo for it.

So we have here a situation were both parties are actually right, and yet could not agree with each other. Ubuntu is affected, but to a lesser degree. It doesn't have something like DFSG, and might just move Firefox to the restricted section if necessary (just like restricted modules and binary drivers). 

Hope they resolve this soon...

---

