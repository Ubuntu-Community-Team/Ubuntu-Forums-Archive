---
title: "sound-juicer package in 9.10 repos is busted"
date: 2009-12-12
forum: Ubuntu Studio
---

### Post by beastrace91 on 2009-12-12
Just as a heads up the default sound-juicer package in the 9.10 repos seg-faults when ever you try to extract music from a disc with it (rendering the program itself useless)

```
jeff@sager-lintop:~/Downloads/wine-1.1.34$ sound-juicer

(sound-juicer:15308): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(sound-juicer:15308): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

** (sound-juicer:15308): CRITICAL **: musicbrainz_submit_message_area_new: assertion `title != NULL' failed

(sound-juicer:15308): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(sound-juicer:15308): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (sound-juicer:15308): CRITICAL **: gedit_message_area_set_default_response: assertion `GEDIT_IS_MESSAGE_AREA (message_area)' failed

(sound-juicer:15308): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

** (sound-juicer:15308): WARNING **: Inhibit method failed

** (sound-juicer:15308): WARNING **: Inhibit problem : The name org.freedesktop.PowerManagement was not provided by any .service files
Segmentation fault

```

It amazes me sometimes how much broken software gets into the default repositories... At any rate I guess I'll be compiling a newer version from source.

~Jeff

---

### Post by gordintoronto on 2009-12-12
It works just fine for me.  Perhaps you need to specify Preferences.

---

### Post by beastrace91 on 2009-12-12
Default settings. I installed it and told it to rip the CD...

And poof! It seg-faults. On a side note I've installed Rubyripper from getdeb.net and it works like a dream.

Also are you running 32bit or 64bit? I'm on the latter of the two.

~Jeff

---

### Post by gordintoronto on 2009-12-12
I think the default settings are inadequate.  Better to specify where to put the ripped files, and what type of file to produce.  My preference is flac...

My Karmic system is 32-bit, my 64-bit system is still running Jaunty.

---

### Post by beastrace91 on 2009-12-12
I'm betting there is an issue with the 64bit on Karmic - because I also compiled the latest version from source and it segfaulted on me as well. If it is an issue with the default settings then thats just poor programming!

At any rate Rubyripper works like a dream. Idk why it's not in the repos instead.

~Jeff

---

### Post by thatguruguy on 2009-12-14
I haven't had that problem, and I'm running Karmic 64-bit.  Here's the output:

> john@john-laptop:~$ sound-juicer

** (sound-juicer:3756): WARNING **: Inhibit method failed

** (sound-juicer:3756): WARNING **: Inhibit problem : The name org.freedesktop.PowerManagement was not provided by any .service files

** (sound-juicer:3756): WARNING **: Invalid cookie
john@john-laptop:~$ 


---

### Post by Stochastic on 2009-12-15
This bug you've run into should be reported on Launchpad.net against the sound-juicer(ubuntu) package.  That way, the developers can try to fix the problem rather than other users (like me) telling you that we've had no troubles with our sound-juicer installs on Karmic.

---

### Post by felipe51 on 2009-12-24
> **beastrace91 said:**
> I'm betting there is an issue with the 64bit on Karmic - because I also compiled the latest version from source and it segfaulted on me as well. If it is an issue with the default settings then thats just poor programming!

At any rate Rubyripper works like a dream. Idk why it's not in the repos instead.

~Jeff
I crossed with this error a few days ago. and finally I found that the problem was that I was pretending to just hit the "Extract" button and let the program do all the work for me.

The program work just fine, I figured out that I was  missing, "not specifying", the track "Title"; because of this it will eventually crash because it is an essential part of the resulting output file when using the default  "output file names". Just add a "Title" to your tracks when "sound-juicer" cant grab them for you.

Best regards
Felipe

---

### Post by trinitrotoluene on 2009-12-26
> **felipe51 said:**
> I crossed with this error a few days ago. and finally I found that the problem was that I was pretending to just hit the "Extract" button and let the program do all the work for me.

The program work just fine, I figured out that I was  missing, "not specifying", the track "Title"; because of this it will eventually crash because it is an essential part of the resulting output file when using the default  "output file names". Just add a "Title" to your tracks when "sound-juicer" cant grab them for you.

Best regards
Felipe

That did it thanks.  Fill in all the tags or else it borks depending on your file naming scheme.  Pretty lame, IMO.

Thien

---

### Post by beastrace91 on 2009-12-26
> **trinitrotoluene said:**
> That did it thanks.  Fill in all the tags or else it borks depending on your file naming scheme.  Pretty lame, IMO.

Thien

Yep, agreed. Check out [Rubyripper](http://linuxappfinder.com/package/rubyripper) - its MUCH better IMO.

~Jeff

---

### Post by felipe51 on 2009-12-28
That Rubyripper is great!

Now I have both installed, just in case. :P

---

### Post by AsianSpanker on 2010-04-18
> **gordintoronto said:**
> I think the default settings are inadequate.  Better to specify where to put the ripped files, and what type of file to produce.  My preference is flac...

My Karmic system is 32-bit, my 64-bit system is still running Jaunty.

Hi, I have been with Ubuntu for 3 years now. I install it on friends computers, and even bought 2 used ones and gave them away with Ubuntu on them. Please,Please,please could people who are helping write out what our acronym is at least once in your explainations? I study, have all the books, and still have to take so much time figuring out flac and acronyms that people much smarter than I know. Doing that and then finding out things like, no matter what I do, sound juicer is broken anyway.
And why is it that Ubuntu keeps changing programs in it's repositories instead of improving them. Most of us switched from Windows because that was what they were doing. Except they kept the same name, and changed how they worked, and charge big money for you to find out after 6 months of using that it works the same as the old one, they just changed where the radio button is located, and changed it's name.

---

### Post by kvolden on 2010-05-04
> **AsianSpanker said:**
> Please,Please,please could people who are helping write out what our acronym is at least once in your explainations? I study, have all the books, and still have to take so much time figuring out flac and acronyms that people much smarter than I know.
Although "flac" technically is an acronym, it's just referred to simply as "flac", in the same way you say "mp3", not "Moving Picture Expert Group-1 Audio Layer 3". It's a lossless codec. Oh, and Wikipedia is your friend. ;)

[QUOTE=AsianSpanker]And why is it that Ubuntu keeps changing programs in it's repositories instead of improving them. Most of us switched from Windows because that was what they were doing. Except they kept the same name, and changed how they worked, and charge big money for you to find out after 6 months of using that it works the same as the old one, they just changed where the radio button is located, and changed it's name.[/QUOTE]
The Ubuntu developers don't make the programs. They try to pick out the best ones that also fit with their philosophy, and if some other program with the same functionality passes the current "standard app" in terms of quality, it might be changed in the next release. I don't see a problem with that, and I also fail to see the link with Windows. Windows doesn't provide you with much more than Notepad, IE and Windows media player. Also, how does GUI-changes between licensed Windows-software versions compare to exchanging a default app with a better default app? They are all free, and you can use whatever you want if you don't like it.

---

