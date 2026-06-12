---
title: "ubuntu ce wallpapers"
date: 2009-08-11
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-08-11
I have added ubuntu-ce-wallpapers deb package to the repository.
If you have latest repository and ubuntu-ce is installed, you just need to do update and upgrade and the wallpapers would be automatically installed.

The wallpapers are previous ubuntu ce wallpapers, one created by "bend it", and also some I found in internet.

DK

---

### Post by oneinch on 2009-08-11
I am not showing any updates either in the Update Manager gui or in the command line using apt-get.

---

### Post by oneinch on 2009-08-11
The problem ended up being that I didn't have the UbuntuCE repo in my list. After I added the repo it fixed the problem. Although I had the same error on the sounds as the other person had.

---

### Post by stlsaint on 2009-08-11
where did you get the repo from?

---

### Post by david_kt on 2009-08-11
> **stlsaint said:**
> where did you get the repo from?

You should update the repo from here:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

I have move the repos to split 64 bits and 32 bits.

DK

---

### Post by Jerriy on 2009-08-12
david, with all due respect but I find those wallpapers to be a unimpressive, I even dare say sub-par. Compare Ubuntu-CE to other distros, (like the satanic-edition or the muslim one for example). 

Don't get me wrong, Ubuntu-CE doesn't have to be just as sleek and cool as other distros, but don't you think a Christian theme deserves better than what we have now?:> for example notice how one of the wallpapers has the bible verse (or whatever it is supposed to be I don't know cuz it's incomplete/half-invisible) way down in the extreme bottom of the screen.

And look at the Brazil/Rio wallpaper: it is bent and crooked (the Jesus statue isn't even straight but leaning like the tower of Pisa)

---

### Post by stlsaint on 2009-08-12
tho i am a huge fan of DK just off the shear fact that he took UCE under personal dedication to bring it to us. but i must admit with all respect that some nice wallpapers would be appreciated! maybe thats something that DK can give us some instruction on that we can go look for some ourselves and submit to him to see about integrating into server edition or even version 0.3 desktop!! 
LET US HELP DK!!!

---

### Post by david_kt on 2009-08-12
> **stlsaint said:**
>  but i must admit with all respect that some nice wallpapers would be appreciated! maybe thats something that DK can give us some instruction on that we can go look for some ourselves and submit to him to see about integrating into server edition or even version 0.3 desktop!!

Yes, please send me some nice wallpapers, and I would replace those wallpapers. By the way, please list out the wallpapers to be removed from existing ones and which ones to keep.

DK

---

### Post by Jerriy on 2009-08-12
The two wallpapers I mentioned above do come into mind for removal-consideration (or else, at least someone should photoshop-away the errors in them) 

As for the other matter well, it is indeed a good idea for users to be able to recommend wallpapers. Appreciate all your work and efforts.

---

### Post by david_kt on 2009-08-12
> **Jerriy said:**
> The two wallpapers I mentioned above do come into mind for removal-consideration 

Actually I could not simulate the incomplete/half-invisible verse in the said wallpapers. I have tried all setting (Zoom, tile, fill screen etc) but the verse still visible completely.

May be there is something to do with screen resolution or monitor setting. Anyway, the said wallpapers is from previous ubuntu ce, is somebody experience that problem before?

DK

---

### Post by david_kt on 2009-08-13
> **Jerriy said:**
> david, with all due respect but I find those wallpapers to be a unimpressive, I even dare say sub-par. Compare Ubuntu-CE to other distros, (like the satanic-edition or the muslim one for example).

Please check out what I have collected this morning, convert it to png, rename and pack into debian package:

[http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/ubuntu-ce-wallpapers_0.2_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/ubuntu-ce-wallpapers_0.2_all.deb)

Please inform me which ones are good and which ones need to remove.
These wallpapers are completely different from previous ones.

DK

---

### Post by Jerriy on 2009-08-19
Wow now you have some nice wallpapers. All of them look fine. However one problem still persists: some of the text on some of the wallpapers still seems to get off the edge (I've put 2 of them in the attachment) I noticed that this happenes only at the top and bottom of the screen.

But before/after removing them it's a good idea to check if this is happening to at least one other individual - to find out if more than one user/computer is affected. That way we can eliminate the possibility that the problem is just on my ubuntu machine: i.e. my display-setup or screen resolution or whatever (I know that in the world of Linux these things can be complicated)

---

### Post by david_kt on 2009-08-19
> **Jerriy said:**
> 
But before/after removing them it's a good idea to check if this is happening to at least one other individual - to find out if more than one user/computer is affected. That way we can eliminate the possibility that the problem is just on my ubuntu machine: i.e. my display-setup or screen resolution or whatever (I know that in the world of Linux these things can be complicated)

I am not sure what's wrong but the picture in your screenshoot shows that all the wallpapers are different from mine (cut at the top and bottom). Are you using a wide screen monitor?

DK

---

### Post by david_kt on 2009-08-20
> **Jerriy said:**
> 
But before/after removing them it's a good idea to check if this is happening to at least one other individual - to find out if more than one user/computer is affected. That way we can eliminate the possibility that the problem is just on my ubuntu machine: i.e. my display-setup or screen resolution or whatever (I know that in the world of Linux these things can be complicated)

Could you download and run below script IN TERMINAL (key in password as requested). After that check whether or not the wallpapers become better.

DK

---

### Post by Jerriy on 2009-08-20
> **david_kt said:**
> I am not sure what's wrong but the picture in your screenshoot shows that all the wallpapers are different from mine (cut at the top and bottom). Are you using a wide screen monitor?

DKYup it's a widescreen. 

Aha! Now I see what's going on. Ubuntu has been secretly cropping my images without letting me konw about it. Hmmm... I mean mean I am not the first ever Ubuntu user that has widescreen, am I? Otherwise why does it happen without any warning? Is there some sort of Linux >< widescreen incompatibility that I should know about?

---

### Post by Jerriy on 2009-08-20
> **david_kt said:**
> Could you download and run below script IN TERMINAL (key in password as requested).

DKI did that and Wow! now I can see it all! I now see one of them reads "Be the church" :)

---

### Post by david_kt on 2009-08-20
> **Jerriy said:**
> Is there some sort of Linux >< widescreen incompatibility that I should know about?

The wallpapers are intended for normal monitor, as such they are not suitable for wide screen one. The little script I make is to stretch the wallpapers to suit wide screen monitor.

May be we should have this option by default.

Another way is to use wide screen wallpapers instead of stretching it.

DK

---

### Post by Jerriy on 2009-08-20
Yea - it would be nice if the wallpapers are wide-screen-ready. 

Anyway, it's an interesting lesson that stretching the default in Windows wallpaper setup but now we konw that something else is the default in ununtu.

---

### Post by sdansmith on 2009-08-30
David,
I'm about as much of a newbie as one person can be, but if we could get access to the logo for Ubuntu CE, we should be able to make some wallpapers, shouldn't we? At least we could create some images and send them to you for inclusion in a future package. 

I hope I didn't just embarrass myself too much by saying all of that.

Dan

---

### Post by david_kt on 2009-08-30
> **sdansmith said:**
> David,
I'm about as much of a newbie as one person can be, but if we could get access to the logo for Ubuntu CE, we should be able to make some wallpapers, shouldn't we? At least we could create some images and send them to you for inclusion in a future package. 

I hope I didn't just embarrass myself too much by saying all of that.

Dan

Yes we need many volunteer like you. We could learn together as we progress. Please see attached logo.

DK

---

### Post by sdansmith on 2009-08-31
David,
  I will work on some examples and email them to you.

Dan

---

