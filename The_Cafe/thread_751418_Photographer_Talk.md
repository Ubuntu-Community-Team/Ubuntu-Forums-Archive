---
title: "Photographer Talk"
date: 2008-04-10
forum: The Cafe
---

### Post by Ioky on 2008-04-10
Hey Every one, I wonder how many photographer out there using Linux like myself, and what is their experiences are like doing photography stuff with Linux. For myself, I love it so far. There is a couple reasons why I like to do photo stuff with Linux. One of them is I can convert format with one command line. Imagen you have like 400 photos, and they all need to change format from jpg to png. (for any reason.) That will take million years to do it in windows or Mac. And there are few Amazing Open Source Software out there for RAW and HDR. In fact, I am not a big fan on Photo editing, I like to editing everything before I shoot my image. But when the time come, I get my tools for free. 

I wonder what software you guy use, and the pro and cos about the software. It would be good, if you can share your work. To get it rolling,you can go to this page for mine. 

[http://foolzage.com/gallery/main.php?g2_itemId=51](http://foolzage.com/gallery/main.php?g2_itemId=51)

---

### Post by regomodo on 2008-04-10
[HDR]("http://qtpfsgui.sourceforge.net/") - qtpfsgui works well and should take your raws directly.

Other than that good Linux/FOSS tools are non-existent. Gimp+ufraw is okish but it's lack of 16bit and cmyk is  a major hindrance. Krita trumps Gimp in that respect but i've found it to be horrendously slow. There is something called bluefish(?) which sort of looks like lightroom (sort of) but hasn't been developed for almost a year.[edit] It's called Bluemarine and the associated project webpage is dead.

There is a panorama program (forget the name but it is in the add/remove tool) but i found its auto setpointing to be bad.

For photo managing i find f-spot to be very amateurish and has bad handling of raw files (the exif's with them i guess). Digikam is better and ok. I just wish Adobe Bridge CS2 would work in wine.

If you want a good editing workflow Adobe Lightroom or Photoshop + Bridge are the only way of getting things done efficiently i'm afraid.

This[ link]("http://galleryjon.fotopic.net/") is to my gallery at fotopic.net which i may not renew this year.

---

### Post by Dixon Bainbridge on 2008-04-10
I shoot in RAW 99% of the time so Raw Studio is fine for me. It supports Nikon NEF format, and does batch conversions.

I run virtual box with XP for Lightroom which is nice to use. Other than that, I occasionally fire up GIMP, but is sort of superfluous now along with Photoshop for my needs.

---

### Post by Daveski on 2008-04-10
> **regomodo said:**
> Gimp+ufraw is okish but it's lack of 16bit and cmyk is  a major hindrance. Krita trumps Gimp in that respect but i've found it to be horrendously slow. There is something called bluefish(?) which sort of looks like lightroom (sort of) but hasn't been developed for almost a year.
...
If you want a good editing workflow Adobe Lightroom or Photoshop + Bridge are the only way of getting things done efficiently i'm afraid..

Is the lack of 16bit and cymk really a hindrance for most amateur photographers?  I am only just getting back into 'serious' photography and I am looking into which tools to use, but it seems to me that as you will have to convert to 8bit for most non-pro applications anyway, that  applying colour balance / curves from the RAW is probably all that really needs the full sensor data - the 8bit data is fine for simple retouching such as that you would achieve in the darkroom anyway.

---

### Post by popch on 2008-04-11
> **Daveski said:**
> Is the lack of 16bit and cymk really a hindrance for most amateur photographers? 

I wouldn't think so. Lack of proper CMYK support becomes an issue when producing for a CMYK environment and when fine control over the gamut is essential. Those are not your typical amateur issues, I believe.

What might be an issue is that some 'procedures' (step by step instructions and such)  published in magazines and books apply to the controls as found in one product rather than another one.

---

### Post by quinnten83 on 2008-04-11
well I understand that GIMP is about to implement CYMK control and 16 bit when they move over to GEIGEL?
I dunno what that means, but i thought it was nice to hear, since the pro's usually complain about those two missing features.

---

### Post by swoll1980 on 2008-04-11
cs2 runs under wine with out any problems

---

### Post by jespdj on 2008-04-11
I am still using Windows because of Photoshop CS3 and Bridge CS3. Unfortunately there's simply nothing that's as powerful as Photoshop available on Linux. Ofcourse you can do a lot with GIMP, but it doesn't have everything that Photoshop has.

Some useful links:
[Linux Photography blog](http://jcornuz.wordpress.com/)
[Meet the GIMP!](http://meetthegimp.org/) - very nice video tutorials for GIMP
[GIMP Tutorials](http://www.gimp.org/tutorials/)
> **quinnten83 said:**
> well I understand that GIMP is about to implement CYMK control and 16 bit when they move over to GEIGEL?
[GEGL](http://gegl.org/). People have been asking for 16-bit per channel and CMYK support in GIMP for years. It seems like the plan is to use GEGL in GIMP 2.6, which would make it easy to implement these things in GIMP. But how long it's going to take before GIMP 2.6 is out, nobody really knows.

---

### Post by regomodo on 2008-04-11
> **Daveski said:**
> Is the lack of 16bit and cymk really a hindrance for most amateur photographers?  

It is if you still use film. Although my scanner can pull in a 42bit value per pixel, things like BnW film need all the workable dynamic range it can get. 8bit is largely useless for me and i haven't used it for almost 4 years.

cmyk is not quite an issue but i do like working the Lab colourspace.

---

### Post by DoctorMO on 2008-04-11
> But how long it's going to take before GIMP 2.6 is out, nobody really knows.

This may seem like an odd question, but have you asked them? A lot of projects are based on the notions that the people who care about the subject would want to be involved enough to push the issue in the programming community. Do you honestly think there are many free software writing, c/c++ programmers who are professional photographers, vector animators and media library managers?

Without user input projects like the gimp will only implement features that programmers want. I see more interesting things coming out of inkscape because there is a great friendly community there of users who push ideas (and those ideas aren't thrown away because they're not programmers)

---

### Post by jespdj on 2008-04-11
> **DoctorMO said:**
> This may seem like an odd question, but have you asked them? A lot of projects are based on the notions that the people who care about the subject would want to be involved enough to push the issue in the programming community. Do you honestly think there are many free software writing, c/c++ programmers who are professional photographers, vector animators and media library managers?
I've looked at the GIMP source code myself and submitted a bug patch, and I've followed the GIMP developer mailing list. Currently there is a small group of developers (I think less than 10 people) who seem to spend a lot of time on working on GIMP. They are ofcourse aware of the fact that there are many people who want things like 16-bit per channel and CMYK support in GIMP, in fact if you ask for this in the GIMP developer mailing list you'll most likely get a rude answer because there have been thousands of people who've asked for this before. People have been asking for this since at least 2003 and maybe even earlier. I can assure you that the developers are thouroughly aware of it.

I wanted to implement some stuff in GIMP but the core developers quickly answer "Don't do that yet, because when we switch to GEGL it will have to be rewritten, blah blah...". But implementing GEGL into GIMP is going to be a lot of work. I think the core developers do have some kind of plan / roadmap, but it is going to take at least 6 to 12 months before GIMP 2.6 comes out.

---

### Post by newbie2 on 2008-08-08
[QUOTE=jespdj]....CMYK support ....[/QUOTE]


[http://www.zedonet.com/en_p_turboprint.phtml](http://www.zedonet.com/en_p_turboprint.phtml)
> TurboPrint Studio with special features is designed for photographers and professional users in publishing and pre-press business. It additionally supports the CMYK color model, you can add your own ICC color spaces and even produce color-consistent proof prints of CMYK documents.

---

### Post by dmn_clown on 2008-08-08
> **regomodo said:**
> [HDR]("http://qtpfsgui.sourceforge.net/") - qtpfsgui works well and should take your raws directly.

Other than that good Linux/FOSS tools are non-existent.

[Cinepaint](http://www.cinepaint.org/) is non-existent?

---

### Post by joninkrakow on 2008-08-09
> **Daveski said:**
> Is the lack of 16bit and cymk really a hindrance for most amateur photographers?  I am only just getting back into 'serious' photography and I am looking into which tools to use, but it seems to me that as you will have to convert to 8bit for most non-pro applications anyway, that  applying colour balance / curves from the RAW is probably all that really needs the full sensor data - the 8bit data is fine for simple retouching such as that you would achieve in the darkroom anyway.

I don't know. I do all my processing in 26 bit mode, and the wide gamut color space, and only drop to 8-bit/jpeg for the final output, or in those odd instances, when I can't do what I need in Photoshop in 16 bit. But those are always towards the end of my workflow, not at the beginning. 

I've played with Linux for my photography work flow, but so far, I can't duplicate my Mac-based work flow. I can use Linux/X11 for a lot of stuff, but I have stuck with MacOS for both photography and video. I'm still searching, however, for Linux apps that would allow me to have a streamlined workflow from RAW to final jpg, including organizing and processing. I think that Linux is getting better, but the work necessary to get to that point is a bit beyond my time constraints. I keep casually checking, and following news--and this thread's been fantastic for that. Some good stuff mentioned. 

I would have to say I need just a few tools:

1. Low-maintenance image importing from my Canon DSLR, with file naming that allows me to name my files and structure my folder structure as I want. I have a simple folder structure YYYY/YYYY_MM_DD/yyyymmdd-XXX.CRW. So, I go three folders deep, and all my files and folders are named by date. It's simple but effective, and somehow, most software doesn't do this. And I couldn't find anything in Linux when I last looked.

2. Flawless RAW processing with a GUI and the ability to batch process from that. I use Canon's software, and have been surprised at how well it works. To me its best feature is that it used my folder structure, and doesn't use its own database. Its batch processing could be faster, but it is quite flexible.

3. Deeper photo processing at either the RAW level or 16 bit tiffs. I use Photoshop 7 and Gimp 2.4 on my Mac, and so far, neither can do this, but I'm really starting to like GIMP. Too bad it drags my poor G4/550 down more than Photoshop 7. Otherwise, I would never launch PS.

4. Flexible and powerful printing. (Actually, I think Digikam does a fair job of this, but then I'm forced to use it for everything)

Here's a question of curiosity....

Never mind. I'll make that another post. :-) 

-Jon

---

### Post by joninkrakow on 2008-08-09
Here's my question.

For those of you using Linux for your photography work flow, I have three questions.

1. What equipment do you use (camera, etc.) 

2. What software do you use

3. What is your workflow. 

Actually, three encompases one and two, but I thought it would be nice to see _what_ you use first, then _how_ you use it. 

-Jon

---

### Post by rax_m on 2008-08-09
I'm an amateur photographer in my spare time.. 


1. Canon 20D SLR
2. UFRaw, RawStudio, Digikam, GIMP (Depends on my mood and what I want to do)
3. I usually have my photos sorted like this : YYYYMM Subject/Event
I find this combination allows me to find most of my pics fairly quickly. So far I've found digikam to be the most complete workflow tool for me, but I'm not sure I like its raw processing. 
Bluemarine looks promising, but its a bit "clunky" and doesn't allow editing yet (I think). 

You can visit my gallery through my sig :)

Is anyone using any of the commercial products through linux? Bibble, lightroom etc.

Rax

---

### Post by tkawa6 on 2008-08-10
I've been using Bibble Pro for while now and I'm happy with it. With it, I can resizes pictures, color correct, adjust aperture a few steps up and down, and the fact that Noise Ninja is built it makes it an awesome piece of software. One of the best $130 investments I've made in a long time.

---

### Post by augied on 2008-08-23
1. Nikon Nikkormat FTN, Nikon FE2
2. Gwenview and Gimp (mostly)
3. Review in Gwenview and make any necessary changes in Gimp (I mostly try to leave them alone)

Can anyone recommend a good but not too expensive film scanner? (or a general purpose scanner that has a back light for film.)  When I get film developed I usually order hi-res scans (The lower quality jpegs are almost useless for anything but viewing on a computer.) but they cost way to much for what is ultimately a hobby.

---

### Post by joninkrakow on 2008-08-23
> **augied said:**
> 1. Nikon Nikkormat FTN, Nikon FE2
2. Gwenview and Gimp (mostly)
3. Review in Gwenview and make any necessary changes in Gimp (I mostly try to leave them alone)

Can anyone recommend a good but not too expensive film scanner? (or a general purpose scanner that has a back light for film.)  When I get film developed I usually order hi-res scans (The lower quality jpegs are almost useless for anything but viewing on a computer.) but they cost way to much for what is ultimately a hobby.

Back when I scanned film, this was the scanner I used: [eBay LINK]("http://cgi.ebay.com/Pacific-Image-Electronics-35mm-slide-film-scanner_W0QQitemZ160269394364QQihZ006QQcategoryZ15223QQssPageNameZWDVWQQrdZ1QQcmdZViewItem")

No, it wasn't the best--only about 4 megapixels, and it was fiddly to get set up, but once dialed in, it could churn them out. It has a film feeder, so if you can get your film uncut or in stips of 6 or more frames, you can dial in your settings, and let it rip. :-) I'm guessing it won't sell for much more than what you see in this eBay auction.

-Jon

---

### Post by pp. on 2008-08-23
I use an Epson perfection 3200 photo. That's a flatbed scanner with an additional back light in the lid. Its resolution of 3200 dpi comes close to that of my elderly Nikon transparency scanner with about 4000 dpi.

It will scan two strips of 135 format negatives with 6 (or is it 8) exposures each. The driver and software provided for Windows and Mac provide a function which detects and separates the individual pictures in the strip. It will, however, scan the individual images as a batch job, doing one complete scanning operation for each pic, and that includes moving the carriage along the whole length of the device for each pic.

Thus, it may not be a fast solution. However, doing twelve or so scans in a row leaves you time to do something else while the scanner is busy.

---

### Post by Dixon Bainbridge on 2008-08-23
> **joninkrakow said:**
> 
2. Flawless RAW processing with a GUI and the ability to batch process from that. I use Canon's software, and have been surprised at how well it works. To me its best feature is that it used my folder structure, and doesn't use its own database. Its batch processing could be faster, but it is quite flexible.



Lightroom? IMHO, nothing is better.

---

### Post by regomodo on 2008-08-23
#

---

### Post by regomodo on 2008-08-23
#

---

### Post by Naiki Muliaina on 2008-08-23
Glad to see this thread! I was trying to make a small photography page on my site for linux (link in sig *shameless plug!*). Seriously though, i found a few proggys for editing, but me and my partner realy are amatuer. I have a canon ixus 75 (nothing fancy but i like) and have been noseying around looking for photography proggys. The only one ive used properly is the Gimp (who hasnt) but theres a couple of others i saw.To name them, Fotoxx, xara, MTpaint. Has anyone got any real experience with them? What do you folk think of them?

Finaly the response to the questions:

1- Cannon Ixus 75

2- F-Spot & Gimp

3- Organized by date untill i forget dates then try to reorganize under subjects. Work flow? More like work tumble ^^

---

### Post by Dixon Bainbridge on 2008-08-23
> **Naiki Muliaina said:**
> Glad to see this thread! I was trying to make a small photography page on my site for linux (link in sig *shameless plug!*). Seriously though, i found a few proggys for editing, but me and my partner realy are amatuer. I have a canon ixus 75 (nothing fancy but i like) and have been noseying around looking for photography proggys. The only one ive used properly is the Gimp (who hasnt) but theres a couple of others i saw.To name them, Fotoxx, xara, MTpaint. Has anyone got any real experience with them? What do you folk think of them?

Finaly the response to the questions:

1- Cannon Ixus 75

2- F-Spot & Gimp

3- Organized by date untill i forget dates then try to reorganize under subjects. Work flow? More like work tumble ^^

Again, this is just my opinion, but Photoshop/GIMP is more a graphic design tool, whereas Lightroom/Lightzone (which has a linux client), are photographic tools. Yeah sure, you can do all sorts of things with WB and colour in Photoshop, but you cant do batch processing and there is no library tool. This is essential stuff for a photographer. I shoot 7-800 shots in a session in RAW. No way can I process that in PS or GIMP.

It does depend on what you want to do with your shots. GIMP is a good tool, as is UFRAW and RAWstudio. But your photographic needs will drive your choice of app.

---

### Post by blueoil on 2008-08-23
I am quite happily doing my photographic post processing in Linux.  Camera is a Nikon D70.

I use Bibble Pro for the raw conversions and am wonderfully pleased with it.

I use gphoto2 for tethered shooting when I need that sort of thing (coupled with Bibble as the viewer)

Gimp is fine for rough printing although my efforts are directed at getting the shot as properly framed and exposed as possible in the camera so I don't, as a rule, do a lot of work with the image after raw conversion.

I do wish there was a decent cataloging software for Linux, but alas...

---

### Post by regomodo on 2008-08-24
#

---

### Post by Dixon Bainbridge on 2008-08-24
> **regomodo said:**
> That could be your reason. When i shoot ~200 per venue i think even i've overdone it.


Haha :) I'd still not like to process 200 RAW in GIMP/PS.

---

### Post by Daveski on 2008-08-24
GIMP can do batch processing

---

### Post by Dixon Bainbridge on 2008-08-25
> **Daveski said:**
> GIMP can do batch processing

Can it take your shots from the camera, put them in date folders on your hard drive, allow for organisation and flagging of shots (by colour, rating etc), allow for non-destructive editting? If so, I'm in. But I dont think it can. And I dont think it has a ND Grad filter either. :)

As far as streamlining and automating photoprocessing, LR is the best. Hopefully it will run in Wine by next year.

---

### Post by regomodo on 2008-08-25
`

---

### Post by regomodo on 2008-08-25
#

---

### Post by regomodo on 2008-08-28
#

---

### Post by Dixon Bainbridge on 2008-08-28
> **regomodo said:**
> Can't you just overlay a new layer with a gradient fill?

Its a little more complicated than that.

---

### Post by regomodo on 2008-08-28
#

---

### Post by joninkrakow on 2008-08-29
> **regomodo said:**
> ha! If you say so. It's what i've done in Photoshop for years when i forgot to use my actual ND's on my camera.

I don't see why it shouldn't work. The key word is in the "overlay" comment, I bet. :-) Maybe if you gave a quick tutorial using GIMP, you could enlighten all on this thread. :-) I always enjoy seeing how others use programs. BTW, another method of doing this is through an inverse mask, but it is too easy to get artifacts with that, but it is quite cool to watch it work.

-Jon

---

### Post by Dixon Bainbridge on 2008-08-30
You can't really make up for not having a ND grad filter on when you take a shot; no layering in photoshop can adequately replicate the effect it has as far as I've tried, but LR's implementation is the most satisfactory. Post-processing complicated things like equalising strong light/dark areas will never yield great results. It's always better to get the shot right before you press the shutter release. :)  LR ND grad filter just makes life a little easier afterwards.

---

### Post by pp. on 2008-08-30
> **Dixon Bainbridge said:**
> You can't really make up for not having a ND grad filter on when you take a shot

I agree. The ND filter prevents the light from driving the emulsion or the sensor into saturation, i.e. it prevents you from overexposing certain areas of your pic. Once saturated, the signal is permanently lost.

There might be other effects if the medium (emulsion or sensor) does not react linearly to light. However, I don't know if such effects exist in real live.

---

### Post by joninkrakow on 2008-08-30
> **Dixon Bainbridge said:**
> You can't really make up for not having a ND grad filter on when you take a shot;

I want to say that it goes without saying that getting it right in-camera is always best, but I guess it doesn't go without saying. ;-) 

I've done some amazing stuff with exposure, color, etc. but I will always be the first to admit that it would have been much nicer had I gotten it right in-camera, which is what I usually try. :-) In fact, one of the beauties of digital is that you can keep shooting until you get it. :-)

That said, one can accomplish quite a bit with native PS and gimp tools, without the addins. It just typically takes more work if you don't have the addins. My biggest complaint about gimp (on Mac OS) is how slow it is. I haven't yet had a chance to push gimp to its limits on my Wind yet, but I hope to see soon.

-Jon

---

### Post by Dixon Bainbridge on 2008-08-30
> **joninkrakow said:**
> I want to say that it goes without saying that getting it right in-camera is always best, but I guess it doesn't go without saying. ;-) 

I've done some amazing stuff with exposure, color, etc. but I will always be the first to admit that it would have been much nicer had I gotten it right in-camera, which is what I usually try. :-) In fact, one of the beauties of digital is that you can keep shooting until you get it. :-)

That said, one can accomplish quite a bit with native PS and gimp tools, without the addins. It just typically takes more work if you don't have the addins. My biggest complaint about gimp (on Mac OS) is how slow it is. I haven't yet had a chance to push gimp to its limits on my Wind yet, but I hope to see soon.

-Jon

You'd be surprised at the number of *cough* alleged professional *cough* photographers I have met that know very little about correct exposure and spend hours upon hours playing with a shot in photoshop because they didnt get it right at the point of pressing the shutter. In fact, there is a whole generation of mainly digital based photographers that just seem to think that digital is so easy to post process that it doesnt matter how its shot in camera, it can always be corrected later. I just think its the wrong way to do it. I've always said that Photoshop should be used as a nip/tuck for a shot and not massive reconstructive surgery.

---

### Post by joninkrakow on 2008-08-30
> **Dixon Bainbridge said:**
> You'd be surprised at the number of *cough* alleged professional *cough* photographers I have met that know very little about correct exposure and spend hours upon hours playing with a shot in photoshop because they didnt get it right at the point of pressing the shutter. In fact, there is a whole generation of mainly digital based photographers that just seem to think that digital is so easy to post process that it doesnt matter how its shot in camera, it can always be corrected later. I just think its the wrong way to do it. I've always said that Photoshop should be used as a nip/tuck for a shot and not massive reconstructive surgery.

Well, I started out with an almost-modern Minolta SRT-100 in 9th grade. It was a pure mechanical, manual camera. In fact there were times my battery died, and I shot without the light meter. I also rolled and developed my own film in my darkroom that my dad and I made out of our basement bathroom. :-) Back in those days, I was taught to shoot a consistently dense roll. When you looked at the roll hanging to dry, you shouldn't see light frames and dark frames, but a consistency in frames. _That_ was how I was taught to expose. Of course, there is always leeway for creative freedom, but there is a point to it. Proper exposure really doesn't leave much room for vast ranges in contrast with film (Tri-X). Of course, there are high-key photos and low-key photos, but overall, if you cna shoot for properly-exposed pictures, you will see that consistency hanging on the drying line. ;-) OK, today, you will see it in the histograms. 

Here's food for thought for those pros you know. In a digital picture, while you may have 5 or more EV of exposure, the pixel data is not spread evenly across all 5 stops. The vast bulk of it is devoted to the brightest part of your photo (the right on a histogram), and only a tiny fraction gets reserved for the lower/left end. That means that if you under-expose, and compensate in post processing, you amplify a lot of noise, but much less real image data. That will never look as good as if you had exposed properly in the first place. I've never calculated it, but I bet you lose several megapixels on a modern camera. Yucky stuff. Much better to get it in camera, and, as you said, nip and tuck.... But I bet you are as guilty as I am of nipping and tucking, and nipping, and tucking some more, and then, giving it just a little more nip and tuck, and finally one more. ;-) I can be bad about it. I like to do it... The key, IMO, is to make it look almost like you didn't do anything when you are looking at the final result, but when you do an A-B comparison with the original, you are amazed at how much better the final result looks. At that point, I quit. :-)

-Jon

---

### Post by VeeDubb on 2008-09-08
> **tkawa6 said:**
> I've been using Bibble Pro for while now and I'm happy with it. With it, I can resizes pictures, color correct, adjust aperture a few steps up and down, and the fact that Noise Ninja is built it makes it an awesome piece of software. One of the best $130 investments I've made in a long time.


I second the recommendation for Bibble Pro. I have been using this for some time.  I find that for processing the raw files from my Nikon DSLRs, (D50 and D80) it's all I need for 98% of my work as a wedding photographer.  It's currently only available in 32bit, but the 32bit version works flawlessly in 8.04 64bit, and in the rare instances that I need to do something it can't handle, loading and then saving a jpeg in gimp is no big deal as long as you take the time to adjust your jpeg settings to minimize the loss in quality.

---

### Post by hakimaki on 2008-09-08
Photography is the only reason I still dualboot.  I don't tweak my photos much but the little that I do I still get the best results in CaptureNX being that I shoot Nikon NEF.  As much as I hate to admit it, linux just doesn't cut it when it comes to editing raw.  Prior that when I was shooting jpeg, gimp was all i needed.

---

### Post by VeeDubb on 2008-09-08
> **hakimaki said:**
> Photography is the only reason I still dualboot.  I don't tweak my photos much but the little that I do I still get the best results in CaptureNX being that I shoot Nikon NEF.  As much as I hate to admit it, linux just doesn't cut it when it comes to editing raw.  Prior that when I was shooting jpeg, gimp was all i needed.


I have two Nikon DSLRs  (D50 and D80) and I am in the process of getting a wedding photography business off the ground.  I have used NX, and personally, I don't like it.  You should really give bibble a try.  You can test drive for free for a month, and the demo is full function.  It's not crippled in any way.

---

### Post by dedmonds on 2008-09-25
Photography is a serious hobby for me. I shoot film and develop at home. I scan with an Epson V700 using VueScan and use GIMP for image manipulation. I still print traditionally, but I now use GIMP for proofing and to explore the possibilities with an image before I step ever step foot in a darkroom.

[http://www.duaneedmonds.com]("http://www.duaneedmonds.com")

---

### Post by joninkrakow on 2008-11-08
I've been wanting to try out Ubuntu as a platform for processing raw images. Over the past few weeks, I've found 3 raw image processors, and wanted to try them out, to see which has a better work flow and potentially, which produces the better output. I also have been eager to try out Hugin, the panorama maker. This week, I finally got the occasion I wanted. I took my family to a nearby park that surrounds an old quarry. The weather was quite frankly awful--foggy and hazy, with little sunshine peaking through the clouds above, and only sporadically. Worse, it was the middle of the day--the worst period for taking pictures. The images I got would tax the best software, so I figured this would make a good test.

First of all, the software I used.

I guess I used F-Spot to import the images onto my hard drive. It had a small hitch, when it died in the middle of the download. I don't know if I bumped the cable, or what, but it messed up the import for FSpot--but I don't mind. I prefer dealing with things from the file manager. It did organize things into folders, but not as I would prefer, and didn't rename the images. I don't know if this is possible, but I didn't bother figuring it out. 

For processing, I have RawStudio, an open-source program, RawTherapee, a freeware offering (for now), and LightZone, a commercial app that has both a demo, and a free, older version that can still be found if you look for it. 

LightZone is based upon Ansel Adam's "zone system" (a brief intro can be found here: [LINK]("http://www.normankoren.com/zonesystem.html"), which I'm partial to. Also, I've played with LightZone on my Mac, but have never seriously used it, so this was going to be an occasion for me to really learn the application. 

However, I also wanted to try out the other two programs, to see what they could do. I'll start with RawStudio.

It's a bit rough, and very short on features. It has no base-line automatic processing, from what I could tell, forcing me to set every parameter manually (except for white balance). This allows for great flexibility, and it really isn't that difficult to do, but it did create problems for preparing images for a panorama. Each image for a panorama must match, so recreating the exposure adjustments for four photos was rather tedious. Batch processing is very rudimentary, but it does exist, at least. Unfortunately, the result did not work in Hugin. Hugin couldn't get enough information from the images to set the focal length nor find control points--I don't know why. I had to manually set some, and due to the low number I created, the end result was a mess. I didn't bother going back to redo it. RawStudio would be fine for a quick adjustment on one photo, but it isn't very useful, IMO, for much more.

Next, I tried RawTherapee. It immediately gives the impression of greater polish. It does a better job at automating, and allows saving multiple exposure adjustments under one post-processing profile, thus making it easy to create four consistent images for my panorama. However, I couldn't find any way to batch-process the four images at once. I had to open each image, apply the postprocessing, and save each one individually. That slowed me down somewhat. It does seem to do a better job of image management than RawStudio, though. Overall, I was happy with the results and how it worked.

Lastly, I tried LightZone. If RT looks polished to RS, LZ makes RT look quite rough. :-) I spent some more time working with LZ's zone tools, and quite love them. It also seems to have a much more complete image management facility. It also handles batch processing better, and can even be used on images in the browse view, not just images opened for editing. I also like how, when you save a custom process, you can choose which adjustments you have made to include.  It does have some weird ways of doing things, and would take some getting used to, for those accustomed to other tools, but I can see why it costs money on the other platforms. It is a much more complete product. That said, I find both RawStudio and RawTherapee quite capable tools for producing excellent results from raw files. 

I have enclosed the two panoramas I was able to produce from RawTherapee and LightZone. I wouldn't judge either's capabilities based upon these panoramas. For one, the tiny file size doesn't reveal enough detail, for another, both went through GIMP for post-processing, and I used different techniques for each file. However, you should be able to tell that both programs produce credible images. Oh, and both RT and LZ deal with color profiles. nice.... Now, all I need are some color profiles for my monitor and printer. ;-) twardowski_pan2.jpg is from RawTherapee, and twardowski_pan-3.jpg is from LightZone.

I will be happy to answer questions on these programs, but since you can download them all (and RawStudio is in the Ubuntu repos, it's even easier). I would also appreciate hearing of any other raw processing tools people are aware of and have used.

-Jon

---

### Post by Dixon Bainbridge on 2008-11-08
> **tkawa6 said:**
> I've been using Bibble Pro for while now and I'm happy with it. With it, I can resizes pictures, color correct, adjust aperture a few steps up and down, and the fact that Noise Ninja is built it makes it an awesome piece of software. One of the best $130 investments I've made in a long time.

Neat Image plugin for PS is the best noise reduction tool available. It's superb, far better results than with noise ninja.

---

### Post by Dixon Bainbridge on 2008-11-08
> **VeeDubb said:**
> I have two Nikon DSLRs  (D50 and D80) and I am in the process of getting a wedding photography business off the ground.  I have used NX, and personally, I don't like it.  You should really give bibble a try.  You can test drive for free for a month, and the demo is full function.  It's not crippled in any way.

If you shoot nikon, and you shoot in RAW, Capture NX is the only piece of software to use for RAW conversion. There is no other software that does it better than Nikon's own. You can then take your TIFF or JPEG into whatever other app you want to process it more, but the difference in quality between capture NX and say Lightroom or Bibble conversion is very noticeable.

---

### Post by GabrielWolff on 2009-04-24
Hey everyone

I got a photographic issue:

My camera started naming the photos all the same, so in order to save them to my HDD, I want to bulk rename all of them (around 30.000) this way:
Date-Time.jpg
or
Date/Date-Time.jpg

Would anyone know how to do that?

---

### Post by megamania on 2009-04-25
> **GabrielWolff said:**
> My camera started naming the photos all the same, so in order to save them to my HDD, I want to bulk rename all of them (around 30.000) this way:

if by "started naming the photos all the same" you mean that when you format the card the photos are named starting from XXXX001, keep in mind that most cameras allow you to choose whether to start from the first available number on the card or keep track of the total number of pictures taken.
You may have changed that setting.

---

### Post by ChanningLuis on 2009-05-11
The site **[ Step Ok ](http://www.stepok.net/eng/index.htm)** is sure to attract the attention of people interested in photography with its two new softwares, Turbo Photo and Recompsit. You can download them for a reasonable price from the site and use them to get great pictures as in Turbo Photo, full control of exposure, color, quality and the problem oriented user interface improves the digital photo, and Recomposit is a photo masking and compositing tool which precisely isolates the image object from its background and merges it with others.

---

### Post by handy on 2009-05-11
I think DxO is the best thing since sliced bread.

---

### Post by joninkrakow on 2009-05-11
> **ChanningLuis said:**
> The site **[ Step Ok ](http://www.stepok.net/eng/index.htm)** is sure to attract the attention of people interested in photography with its two new softwares, Turbo Photo and Recompsit. You can download them for a reasonable price from the site and use them to get great pictures as in Turbo Photo, full control of exposure, color, quality and the problem oriented user interface improves the digital photo, and Recomposit is a photo masking and compositing tool which precisely isolates the image object from its background and merges it with others.

Somehow, I get the odd impression that this post (quoted above) is nothing more than an ad. It touts Windows-only software, is the first post, etc... Just FYI.

-Jon

---

### Post by racerraul on 2009-05-11
> **ChanningLuis said:**
> The site **[ Step Ok ](http://www.stepok.net/eng/index.htm)** is sure to attract the attention of people interested in photography with its two new softwares, Turbo Photo and Recompsit. You can download them for a reasonable price from the site and use them to get great pictures as in Turbo Photo, full control of exposure, color, quality and the problem oriented user interface improves the digital photo, and Recomposit is a photo masking and compositing tool which precisely isolates the image object from its background and merges it with others.

Are you ready, kids?
Aye, aye captain!
I can't hear you!
Aye, aye captain!
Ohh.... who can't read the forum CoC before he clicks?
SPamBOB SQUAREPANTS!
Arrogant and yellow and greedy is he!
SPamBOB SQUAREPANTS!
If spamming nonsense be something you wish,
SPamBOB SQUAREPANTS!
Then boot on to Windows for your spyware fix!
SPamBOB SQUAREPANTS!
Ready?
SPamBOB SQUAREPANTS
SPamBOB SQUAREPANTS
SPamBOB SQUAREPANTS
SPamBOOOOOOOB... SQUAREPANTS!!!!
Har har!
Da da da da dum da dum!

---

### Post by ngaio on 2009-05-22
> **joninkrakow said:**
> I would have to say I need just a few tools:

1. Low-maintenance image importing from my Canon DSLR, with file naming that allows me to name my files and structure my folder structure as I want. I have a simple folder structure YYYY/YYYY_MM_DD/yyyymmdd-XXX.CRW. So, I go three folders deep, and all my files and folders are named by date. It's simple but effective, and somehow, most software doesn't do this. And I couldn't find anything in Linux when I last looked.


Did you try my program Rapid Photo Downloader? It can do this very easily, and more.

---

### Post by ngaio on 2009-05-22
> **GabrielWolff said:**
> Hey everyone

I got a photographic issue:

My camera started naming the photos all the same, so in order to save them to my HDD, I want to bulk rename all of them (around 30.000) this way:
Date-Time.jpg
or
Date/Date-Time.jpg

Would anyone know how to do that?

Rapid Photo Downloader can do that. Hopefully your JPG files still have the EXIF information in them. You will also need the disk space available for the 30,000 images to be copied (they will not be renamed in place).

---

### Post by GabrielWolff on 2009-05-22
> **ngaio said:**
> Rapid Photo Downloader can do that. Hopefully your JPG files still have the EXIF information in them. You will also need the disk space available for the 30,000 images to be copied (they will not be renamed in place).

Thanks for this post.
I did find a solution for the renaming (although I think I might switch to this one, it seems easier), but my real problem is the automatic turning. My exif data seems alright, but my images are never turned the right way (or at all...)
Here's what the command exif says:```
gabriel@gabriel-laptop:~/Pictures/090521$ exif 090521085018 
EXIF tags in '090521085018' ('Intel' byte order):
--------------------+----------------------------------------------------------
Tag                 |Value                                                     
--------------------+----------------------------------------------------------
Manufacturer        |FUJIFILM                                                  
Model               |FinePix S5700 S700                                        
Orientation         |top - left                                                
x-Resolution        |72.00                                                     
y-Resolution        |72.00                                                     
Resolution Unit     |Inch                                                      
Software            |ExifTool v7.30, RenRot v0.25                              
Date and Time       |2009:05:21 08:50:18                                       
YCbCr Positioning   |co-sited                                                  
Copyright           |[None] (Photographer) -  (Editor)                         
Unknown             |                                                          
Compression         |JPEG compression                                          
Orientation         |top - left                                                
x-Resolution        |72.00                                                     
y-Resolution        |72.00                                                     
Resolution Unit     |Inch                                                      
YCbCr Positioning   |co-sited                                                  
Exposure Time       |1/89 sec.                                                 
FNumber             |f/3.5                                                     
ExposureProgram     |Normal program                                            
ISO Speed Ratings   |64                                                        
Exif Version        |Exif Version 2.2                                          
Date and Time (origi|2009:05:21 08:50:18                                       
Date and Time (digit|2009:05:21 08:50:18                                       
ComponentsConfigurat|Y Cb Cr -                                                 
Compressed Bits per |4.00                                                      
Shutter speed       |6.50 EV (APEX: 9, 1/90 sec.)                              
Aperture            |3.60 EV (f/3.5)                                           
Brightness          |5.80 EV (190.89 cd/m^2)                                   
Exposure Bias       |0.00 EV                                                   
MaxApertureValue    |3.60 EV (f/3.5)                                           
Metering Mode       |Pattern                                                   
Light Source        |0                                                         
Flash               |Flash did not fire, compulsory flash mode.                
Focal Length        |9.4 mm                                                    
Maker Note          |1854 bytes unknown data                                   
FlashPixVersion     |FlashPix Version 1.0                                      
Color Space         |sRGB                                                      
PixelXDimension     |3072                                                      
PixelYDimension     |2304                                                      
Focal Plane x-Resolu|5376.00                                                   
Focal Plane y-Resolu|5376.00                                                   
Focal Plane Resoluti|Centimeter                                                
Sensing Method      |One-chip color area sensor                                
File Source         |DSC                                                       
Scene Type          |1                                                         
Custom Rendered     |Normal process                                            
Exposure Mode       |Auto exposure                                             
White Balance       |Auto white balance                                        
Scene Capture Type  |Standard                                                  
Sharpness           |Normal                                                    
Subject Distance Ran|Unknown                                                   
InteroperabilityInde|R98                                                       
InteroperabilityVers|0100                                                      
--------------------+----------------------------------------------------------
EXIF data contains a thumbnail (5382 bytes).
gabriel@gabriel-laptop:~/Pictures/090521$ 

``` Does it seem wrong in any way?
Why are my images never turned automatically?

---

### Post by GabrielWolff on 2009-05-22
I got an issue I'm struggling with for a while:
When editing photos I normally save the different stages of editing, in order to be able to get back to any stage and continue the next day from there if I decided to change anything.
So if I want to make a color photo sepia, I will have three images at the end:
The Color
The B&W
The Sepia

Does any of you do the same?
And if so: how do you rename your photos? How do you generally indicate what editing a photo has gone through? In tags? The names? Not at all?

---

### Post by koshatnik on 2009-05-22
> **GabrielWolff said:**
> I got an issue I'm struggling with for a while:
When editing photos I normally save the different stages of editing, in order to be able to get back to any stage and continue the next day from there if I decided to change anything.
So if I want to make a color photo sepia, I will have three images at the end:
The Color
The B&W
The Sepia

Does any of you do the same?
And if so: how do you rename your photos? How do you generally indicate what editing a photo has gone through? In tags? The names? Not at all?

I use lightroom as its non-destructive. I think lightzone and bibble are non-destructive also, and are linux native, so that might be the way to go.

You then export the amended photo. The original is untouched, and can be reset at anytime. No need to save any stages in lightroom either. It keeps all the changes as settings, it loads when you fire the app back up again.

Use comment in EXIF data to keep track of the edits.

---

### Post by GabrielWolff on 2009-05-22
> **koshatnik said:**
> I use lightroom as its non-destructive. I think lightzone and bibble are non-destructive also, and are linux native, so that might be the way to go.
Are there any free programs you'd recommend?

---

### Post by megamania on 2009-05-22
> **koshatnik said:**
> I use lightroom as its non-destructive. 
That's very interesting. Can you give me an idea of how it works?

Does it save the original jpg and the "description" of the changes made to the picture?

---

### Post by koshatnik on 2009-05-22
> **GabrielWolff said:**
> Are there any free programs you'd recommend?

None pro level, no.

Amateur use, picasa3 is ok for general pootling about. Other than that, I just use lightroom.

> **megamania said:**
> That's very interesting. Can you give me an idea of how it works?

Does it save the original jpg and the "description" of the changes made to the picture?

Nope, it doesnt save anything until you export your changed image or the unchanged image (depending on what you've done/not done to the original). All it does is remember what you did to the photo - so it saves a log file for that image I guess. You can reset to the original shot anytime by hitting reset.

Simples.

---

### Post by Daveski on 2009-05-22
> **koshatnik said:**
> I use lightroom as its non-destructive.

If you use GIMP and are happy with layers, then you can always have a 'master' layer as the original untouched image. You can duplicated this layer and make as many changes as you like to this and other layers leaving the original untouched.

With this method you can always keep the multiple layers with the multiple stages of change and go back to any at any time. The native format of a GIMP image will then always contain at least the original as well as your changes as separate layers.

You only 'Flatten' these multi-layers and export as a separate file when you are done.

This is how most Photo Shop users work I believe.

---

### Post by koshatnik on 2009-05-22
> **Daveski said:**
> If you use GIMP and are happy with layers, then you can always have a 'master' layer as the original untouched image. You can duplicated this layer and make as many changes as you like to this and other layers leaving the original untouched.

With this method you can always keep the multiple layers with the multiple stages of change and go back to any at any time. The native format of a GIMP image will then always contain at least the original as well as your changes as separate layers.

You only 'Flatten' these multi-layers and export as a separate file when you are done.

This is how most Photo Shop users work I believe.

Not exactly efficient workflow. :p  Can't imagine doing that for hundreds of images.

This is precisely the reason why linux isn't adopted more widely. Doesn't have pro tools for pro work.

---

### Post by joninkrakow on 2009-05-23
> **koshatnik said:**
> Not exactly efficient workflow. :p  Can't imagine doing that for hundreds of images.

This is precisely the reason why linux isn't adopted more widely. Doesn't have pro tools for pro work.

I'm not exactly sure what the two have to do with each other. I mean, is not Photoshop a "pro" tool? I've been using Photoshop since version 3 or thereabouts. This is how you do things in Photoshop, as the previous poster stated. Granted, there are other tools nowadays that make Photoshop and the GIMP look downright prehistoric, but one can hardly call either tool _non-professional_. As I said, I've used Photoshop for years. I _like_ Photoshop. GIMP, especially with version 2.6, is every bit as capable and professional, IMO, as Photoshop. Different, yes--but no less capable, other than the all-important 16 bit capability. In fact, since I upgraded my Mac to Intel, my old Photoshop no longer works. I have been dabbling with GIMP for a couple years, but now, both in OSX and on Linux, I'm dependant upon it. And it's come through with shining colors. :-) In fact, on a whim, I recently used GIMP to create the image below. When I was shooting this series of photos, I accidently let my aperture close down, and my background wasn't blurred enough. I used GIMP to "fix" that. Needless to say, GIMP is no lightweight, and it takes second place to nobody. It is capable of pro-quality work.... but that brings up another point.

My mistake in my photo was a rather silly one. Pros don't make those kinds of mistakes. Real pros get it right in camera. They don't have time to "photoshop" or "gimp" hundreds of photos. They shoot them right, and they "edit" by tossing the flops. That's what the real pros do. ;-) You save the hard work for those pictures you really can't afford to give up, but those should be the  _real_ exceptions...

Ah, but I'm a GIMP addict.... ;-)

Edit: I forgot to mention that my avatar pic is a combo effort between Photoshop and GIMP. Gimp did some things I wanted better, and Photoshop others. That's how it works. ;-)

-Jon

---

### Post by koshatnik on 2009-05-23
> **joninkrakow said:**
> I'm not exactly sure what the two have to do with each other. I mean, is not Photoshop a "pro" tool? I've been using Photoshop since version 3 or thereabouts. This is how you do things in Photoshop, as the previous poster stated. Granted, there are other tools nowadays that make Photoshop and the GIMP look downright prehistoric, but one can hardly call either tool _non-professional_. As I said, I've used Photoshop for years. I _like_ Photoshop. GIMP, especially with version 2.6, is every bit as capable and professional, IMO, as Photoshop. Different, yes--but no less capable, other than the all-important 16 bit capability. In fact, since I upgraded my Mac to Intel, my old Photoshop no longer works. I have been dabbling with GIMP for a couple years, but now, both in OSX and on Linux, I'm dependant upon it. And it's come through with shining colors. :-) In fact, on a whim, I recently used GIMP to create the image below. When I was shooting this series of photos, I accidently let my aperture close down, and my background wasn't blurred enough. I used GIMP to "fix" that. Needless to say, GIMP is no lightweight, and it takes second place to nobody. It is capable of pro-quality work.... but that brings up another point.

I don't use GIMP or Photoshop, ever. I was talking about photo workflow tools, although lightzone and bibble have native linux clients, linux could certainly do with more choice. And no one in digital image making will take linux seriously as a platform until Adobe starts making native linux clients for its apps.

> My mistake in my photo was a rather silly one. Pros don't make those kinds of mistakes.

I hear ya, I'm a pro myself. Andplenty do. Pro means you do it for money, its not a gauge of your ability to take good shots. Most serious amateurs I know are better than 80% of pro's I've met.

> Real pros get it right in camera. They don't have time to "photoshop" or "gimp" hundreds of photos. They shoot them right, and they "edit" by tossing the flops. That's what the real pros do. ;-) You save the hard work for those pictures you really can't afford to give up, but those should be the  _real_ exceptions...

Yes and no. I've had times where I've shoot a whole sequence of 50 shots and afterwards wanted them all set to a different kelvin degree white balance. Good luck doing that in GIMP or PS.

When I shoot bands playing live in some dingy grot-hole, I often autotone 400 shots in Lightroom, then chuck the crap ones. Again, good luck autotoning 400 shots in GIMP or PS.

---

### Post by ozzyprv on 2011-01-03
I think you both koshatnik and joninkrakow are right.
GIMP/Photoshop are not workflow tools, not in Mac, not in Widnow$, not in Linux.
For that you use programs like Lightroom, Bible, digiKam, and maybe Darktable, etc.
I am pretty sure you can make batch tone adjustments in digiKam using the batch processor. Last entry of the post was some time ago (amy 2009), Linux photography workflow tools have come long way...

---

### Post by linuxforartists on 2011-01-03
This has been an awesome thread.  I've been following news regarding Linux as a creative platform.  You guys have named a lot of good programs to check out.  Thanks for the tips!

---

