---
title: "Burning DVD's"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by andras artois on 2008-10-02
How do I do it? I'm on hardy and want to know what the easiest, fastest way to burn .avi files to a dvd disc that will work in a dvd player is.

Thanks x

---

### Post by Brain-free on 2008-10-02
First of all, you may be interested in [this]("http://www.linuxalt.com/"). For every useful Windows app, it shows the linux alternative. So, if DVDShrink or Nero is what you have in mind, you can try some apps from the lists to see if they fit your needs.

Now, to the answer, I think "Devede" is mostly used for this kind of job. You can download it from the repositories.

Also, here's a [helpful guide]("http://news.softpedia.com/news/How-to-convert-AVI-to-DVD-54418.shtml").

---

### Post by Jackie999 on 2008-10-02
One of my favorite programs is Converxtodvd - it runs quite nicely under Wine.

---

### Post by andras artois on 2008-10-02
> **Brain-free said:**
> First of all, you may be interested in [this]("http://www.linuxalt.com/"). For every useful Windows app, it shows the linux alternative. So, if DVDShrink or Nero is what you have in mind, you can try some apps from the lists to see if they fit your needs.

Now, to the answer, I think "Devede" is mostly used for this kind of job. You can download it from the repositories.

Also, here's a [helpful guide]("http://news.softpedia.com/news/How-to-convert-AVI-to-DVD-54418.shtml").

Thank you :) that guide was what I was looking for. I already had DeVeDe installed and had had a go with it but wasn't sure if I was doing it right. One more question though, once I get to this bit:

> We are back to the main window and you can set some final options for your new DVD-Video movie before you click on the 'Forward' button. For example, DeVeDe offers you the possibility of creating the DVD in ISO image ready to burn to a DVD disc, output the DVD movie in the standard DVD-Video folders (AUDIO_TS and VIDEO_TS) or create only a MPEG-2 file. Don't forget to select the size of this DVD (4.7 GB DVD is the most frequently used and the default one) and if you are all set up, please click on the 'Forward' button.

Does it matter which option I choose? Or can they all be burnt to disc by using a regular disc burning program such as Brasero or Gnomebaker?

Thank you for the help so far! Much appreciated.

---

### Post by mohtasham1983 on 2008-10-03
I was looking for the same thing for a while and finally figured it out how to convert a divx movie and burn it on a DVD so that it can be played by all DVD players. I tried both Nero (Windows) and iMovie(Mac) with no luck to get everything working on rewritable DVDs. But here is what you have to do to make a dvd movie using Linux quickly.

Basically, all you need is to use devede to create an ISO file.

Once the iso file is created, issue the following command and after a few minutes you can enjoy watching your favorite movie on a big TV,

[PHP]growisofs -dvd-compat -Z /dev/dvd=image.iso[/PHP]

This way, even if you burn the movie on a rewritable DVD, it will finalize it and your DVD player won't complain about it.

Just in case if you want to format your rewritable DVD to burn another movie on it use the following command:

[PHP]dvd+rw-format -force /dev/dvdrw[/PHP]

---

### Post by Brain-free on 2008-10-03
Well now, I haven't used Devede myself but from what I see, if you choose to have video_ts and audio_ts folders and then make it an ISO, you should be able to burn it with Brasero or any other program. Again, just a thought, not my experience.

---

### Post by aeiah on 2008-10-03
> **andras artois said:**
> Thank you :) that guide was what I was looking for. I already had DeVeDe installed and had had a go with it but wasn't sure if I was doing it right. One more question though, once I get to this bit:



Does it matter which option I choose? Or can they all be burnt to disc by using a regular disc burning program such as Brasero or Gnomebaker?

Thank you for the help so far! Much appreciated.


i suggest setting it to create the iso, and setting the DVD to 4.7. once the iso is created, you can burn it to dvd by right clicking on it and selecting 'burn to disk..'.

---

### Post by andras artois on 2008-10-03
Thank you everyone for the help :) x

---

