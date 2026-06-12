---
title: "MS office - wine or vbox?"
date: 2013-06-03
forum: Virtualisation
---

### Post by mastablasta on 2013-06-03
I've succesfully installed MSOffice 2007 in wine to try it out (the needed components are only Powerpoint, Word and Excel). so far the only thing that i noticed is the occasional crash if i work with smart art (though wine page says it doesn't work it is not explain what does not work in smart art).

i've noticed some people having problems. either on wine upgrades/updates or similar. and then being advised to dual boot or use windows.

but what about using office in virtual box (winXP+ms office 2007)? would it take too much resources? how fast does it all run on modern maschines (specifically i3 1.8Ghz or A4 2,5Ghz CPU with 4 GB ram). My only brush with vbox is on my signle core maschine with 2GB ram running winxp with Xubuntu as guest. and it is not that fast once i open a few programmes. and the E-450 can also run some light OS (e.g. Lubutnu) in vbox reasonably well i've found.


which option is better for casual computer user? wine or open office? dualboot is too tedious just to use the office. and i don't want to explain the magic behind how it all works too much.

---
Libre office is not really an option in this case (compatibility etc.). Though i might still convince them to use it later on.

---

### Post by dragonfly41 on 2013-06-03
> the needed components are only Powerpoint, Word and Excel

Libre office is not really an option in this case (compatibility etc.).

Are you sure that this is a real obstacle?

e.g. have you tried installing AbiWord and convert Microsoft file formats for use in Libre Office?

AbiWord has a useful CLI which allows batch processing of legacy Microsoft files.

But it may be that you have some complex features in your documents which rule out this option..

---

### Post by mastablasta on 2013-06-03
> **dragonfly41 said:**
> Are you sure that this is a real obstacle?

e.g. have you tried installing AbiWord and convert Microsoft file formats for use in Libre Office?

AbiWord has a useful CLI which allows batch processing of legacy Microsoft files.

But it may be that you have some complex features in your documents which rule out this option..


the person that will be using the maschine will not be interested into doing things like conversions, checking if it all works etc. i do not know what kind of features they have in their documents. but to be sure it is better that they use same programmes as they will use to create the documents. so for the moment i am not interested in alternatives (in this case) but only what is best way to run this MS office inside Linux. if it's too much trouble then it's better to just buy a windows preloaded mashcine and be done with it (at the moment i am thinking about Linux preloaded maschine as they cost about 100 EUR less than the ones with Windows).

i do intend to introduce them to Libre office. in my opinion it would be good enough for them, however like i said i can not be 100 % sure (especially with word and excel files). but i am sure MS office will work. 

i've also tried a test document created to test office compatibility and it doesn't have to be a special feature and Libre office won't do it right (e.g. in writer a table or a drawn rectangle). with that test the LO got about 85% of things correctly.

it seems other programmes are fine since i already steered them towards opensource programmes, so they are used to Firefox, Thunderbird, VLC...

---

### Post by kurt18947 on 2013-06-03
I'm using LibreOffice 4.0.  .doc & .docx files seem to open pretty well.  I usually save as .doc rather than .docx though the few experiments I've performed saving as .docx opened pretty well in MSO 2007 or using the file viewer.  There are a few other office options in addition to Libre Office.  Some people say Open Office does a better job than LibreOffice with MSO files.  There's also a China-based office suite ( I don't recall the name right now) that is supposed to have good MSO file compatibility.  There's also Softmaker Office that has a 30 day trial.  If that works well, you can sign up for their Email promotions, they have sales & once you download the trial you qualify for the upgrade price.

---

### Post by LewisTM on 2013-06-03
I have both MSO 2007 in Wine (PlayOnLinux) and VBox+WinXP. I can say that working with Wine+Word in Xubuntu feels of course more natural to a user than opening a VM, then a document in a shared folder. 
However, I did experience crashes and some formatting and display inconsistencies in Wine+Word. I would recommend it only as a quick previewing tool, and work on long and important documents in VBox.

Cheers!

---

### Post by wieman01 on 2013-06-03
I have used MS Office 2010 with Wine for a while and it does work for me. PowerPoint isn't as reliable, but Excel & Word are both pretty stable and the UI responds well. I personally recommend using Wine if you do not need PowerPoint as much. But of course that's a matter of taste after all.

---

### Post by mastablasta on 2013-06-04
> **wieman01 said:**
> I have used MS Office 2010 with Wine for a while and it does work for me. PowerPoint isn't as reliable, but Excel & Word are both pretty stable and the UI responds well. I personally recommend using Wine if you do not need PowerPoint as much. But of course that's a matter of taste after all.
> **LewisTM said:**
> I have both MSO 2007 in Wine (PlayOnLinux) and VBox+WinXP. I can say that working with Wine+Word in Xubuntu feels of course more natural to a user than opening a VM, then a document in a shared folder. 
However, I did experience crashes and some formatting and display inconsistencies in Wine+Word. I would recommend it only as a quick previewing tool, and work on long and important documents in VBox.
Cheers!

Thanks. that's the kind of info i was looking for. i will see how to proceed. you experience is similar to mine. a couple of crashes (powerpoint), but Excel and word worked preety much ok.

> **kurt18947 said:**
> I'm using LibreOffice 4.0. .doc & .docx files seem to open pretty well. I usually save as .doc rather than .docx though the few experiments I've performed saving as .docx opened pretty well in MSO 2007 or using the file viewer. There are a few other office options in addition to Libre Office. Some people say Open Office does a better job than LibreOffice with MSO files. There's also a China-based office suite ( I don't recall the name right now) that is supposed to have good MSO file compatibility. There's also Softmaker Office that has a 30 day trial. If that works well, you can sign up for their Email promotions, they have sales & once you download the trial you qualify for the upgrade price.

you mean Kingsoft office or somehting like that in Ubuntu Kylin or whatever it is with MSO like interface...i might give it a try on that test file. :-)

i am aware of the alternatives (installed and online) but i am also not interested in them (unless they have 100% compatibility and look the same). i know how to do changes etc and i am prepared to learn which is why i use libre office. but the person i would install it for has no interest in that. 

just to add i remembered i have latest LO as portable LO and the test on the word sample file was ok on this version. hmm... i am still not sure about excel.

i will try to see what kind of files they are working with actually (how complex they really are).

---

