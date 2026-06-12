---
title: "Simple Expose for lxde lubuntu no compositing required"
date: 2012-10-26
forum: Tutorials
---

### Post by ronniew on 2012-10-26
Expose on the mac and I forget what its called in Unity but its pretty cool for checking out running programs and switching between them easily.

On Lubuntu there is no compositing which makes this feature basically impossible... Luckily Skippy XD does the trick. How? It throws up a quick compositor when you activate it to get the job done, then closes it when your finished selecting what you want. So no resources wasted.

Pretty easy to do..

Download and install SkippyXD depending on your platform from [here]("http://code.google.com/p/skippy-xd/downloads/list")

Once installed open up run or a terminal and enter

leafpad ~/.config/openbox/lubuntu-rc.xml

find the line

 <chainQuitKey>C-g</chainQuitKey>

below it copy and paste the following

```
<!-- Start Expose for LXDE-->
<keybind key="A-grave">
      <action name="Execute">
        <command>skippy-xd</command>
      </action>
    </keybind>
<!-- End Expose for LXDE-->
```

*****Updated code to correct syntax error, code above is updated*****

save and close

open run or a terminal and run following command

openbox --restart

now when you hold the alt key and hit `   you expose feature will activate

[IMG]http://www.unleashpc.com/exposelxde.png[/IMG]

*****
**I will be providing a series of easy solutions and linking to them below**
[URL="http://ubuntuforums.org/showthread.php?t=2076351"]
lxde simple weather[/URL]
[lxde wallpaper changer]("http://ubuntuforums.org/showthread.php?t=2076417")
[aero snap for lubuntu]("http://ubuntuforums.org/showthread.php?p=12318519")

---

### Post by Yorvik on 2012-10-26
Why use 'gksu leafpad ...', when just 'leafpad ...' would do?

---

### Post by Yorvik on 2012-10-26
Getting the following error after running ```
openbox --restart
```

One or more XML syntax errors were found while parsing the Openbox configuration files. See stdout for more information. The last error seen was in file "/home/******/.config/openbox/lubuntu-rc.xml" line 188, with message: Comment not terminated
<!--- Start Expose for LXDE --->
<keybind key="A-grave"

---

### Post by vasa1 on 2012-10-26
> **Yorvik said:**
> Getting the following error after running ```
openbox --restart
```

One or more XML syntax errors were found while parsing the Openbox configuration files. See stdout for more information. The last error seen was in file "/home/******/.config/openbox/lubuntu-rc.xml line 188, with message: Comment not terminated
<!--- Start Expose for LXDE ---?
<keybind key="A-grave"
Maybe it should be
```
<!--- Start Expose for LXDE --->
```
Replace the ? with >

Lines in .xml files are commented out like this: ```
    <!-- comments are flanked with <!-- on the LHS and --> on the RHS  -->
```

---

### Post by vasa1 on 2012-10-26
> **Yorvik said:**
> Getting the following error after running ```
openbox --restart
```

**One or more XML syntax errors** were found while parsing the Openbox configuration files. See stdout for more information. **The last error** seen was in file "/home/******/.config/openbox/lubuntu-rc.xml line 188, with message: Comment not terminated
<!--- Start Expose for LXDE ---?
<keybind key="A-grave"

If you're still having trouble, it maybe because of the parts in bold. I've been lucky in making just one mistake at a time.
As I mentioned [elsewhere]("http://ubuntuforums.org/showpost.php?p=12319044&postcount=5"), I prefer openbox --reconfigure because all that is needed is just to refresh the rc.xml file rather than restart openbox.

---

### Post by Yorvik on 2012-10-26
The question mark is a typo when copying (I couldn't do a copy/paste from the error box) the error massage.  The message only occurs when the code from the first post is pasted into the file.

---

### Post by vasa1 on 2012-10-26
> **Yorvik said:**
> The question mark is a typo when copying (I couldn't do a copy/paste from the error box) the error massage.  The message only occurs when the code from the first post is pasted into the file.
Oh! Can you try some keybinding other than A+grave? I'm not sure whether the grave key works. I vaguely remember being unsuccessful with it.

---

### Post by Yorvik on 2012-10-26
That's it. Two dashes not three solved the syntax error problems.  Now to find a key combination that works and isn't already in use.

---

### Post by Yorvik on 2012-10-26
So what I have now is:
```
<!-- Start Expose for LXDE -->
<keybind key="A-dead_grave">
      <action name="Execute">
        <command>skippy-xd</command>
      </action>
    </keybind>
<!-- End Expose for LXDE -->
```
and all is well :)

---

### Post by vasa1 on 2012-10-26
> Two dashes not three solved the syntax error problems. and 
> So what I have now is:
...<keybind key="A-dead_grave">
...
and all is well :)

1. It's the little things that matter!
2. Re. "dead_grave" ... I had to Google to find out what that meant but now I have this:
```
    <!-- Launch Customize Look and Feel-->
    <keybind key="A-grave">
      <action name="Execute">
        <command>lxappearance</command>
      </action>
    </keybind>

```
Note that it's a simple grave for me. Trying dead_grave didn't work (but didn't throw up an error either). Maybe it's locale-dependent? In any case, thank you for the grave tip. :)

---

### Post by Yorvik on 2012-10-27
It could well be locale dependant.  I used ```
xev
``` to determine what the key was.

---

### Post by vasa1 on 2012-10-27
> **Yorvik said:**
> It could well be locale dependant.  I used ```
xev
``` to determine what the key was.
That showed just grave for me. My keyboard is set the US way.

---

### Post by geovino on 2012-10-28
> **vasa1 said:**
> and 


1. It's the little things that matter!
2. Re. "dead_grave" ... I had to Google to find out what that meant but now I have this:
```
    <!-- Launch Customize Look and Feel-->
    <keybind key="A-grave">
      <action name="Execute">
        <command>lxappearance</command>
      </action>
    </keybind>

```
Note that it's a simple grave for me. Trying dead_grave didn't work (but didn't throw up an error either). Maybe it's locale-dependent? In any case, thank you for the grave tip. :)

So what is the key combination when I add dead_grave? 

ALT + what?

---

### Post by geovino on 2012-10-28
I added this code:

<!-- Start Expose for LXDE -->
<keybind key="A-dead_grave">
      <action name="Execute">
        <command>skippy-xd</command>
      </action>
    </keybind>
<!-- End Expose for LXDE -->

ran openbox --start

but nothing happens. What is the key combo for this a work?

ALT + What?

---

### Post by vasa1 on 2012-10-28
Well, you can use any keys that are convenient for you. The main thing is to make sure the combination isn't already in use somewhere else. There's no warning.

The grave or dead_grave key is on the left side of the keyboard, just below the esc key (and just above the tab key). Without holding down shift, pressing that key should give a ` (grave used in many European languages and even in Bash). Holding down the shift key and pressing that key should give a ~ (tilde).

---

### Post by vasa1 on 2012-10-28
> **geovino said:**
> I added this code:

<!-- Start Expose for LXDE -->
<keybind key="A-dead_grave">
      <action name="Execute">
        <command>skippy-xd</command>
      </action>
    </keybind>
<!-- End Expose for LXDE -->

ran openbox --start

but nothing happens. What is the key combo for this a work?

ALT + What?

Not 
openbox --start
but
openbox --restart

I prefer
openbox --reconfigure

Also try **grave** instead of **dead_grave**.

---

### Post by Yorvik on 2012-10-28
As I pointed out earlier, if you run 'xev' in a terminal it will tell you the code and/or name of the key/s you have pressed.

---

### Post by ronniew on 2012-10-28
the first post code is already updated to correct the syntax error

after applying the first post code simply hold down alt then hit `


no need for the secondary post of the code

---

### Post by geovino on 2012-10-28
> **vasa1 said:**
> Not 
openbox --start
but
openbox --restart

I prefer
openbox --reconfigure

Also try **grave** instead of **dead_grave**.

It's working now. :)

---

### Post by vanlong441 on 2012-11-15
Is it possible to have a transparent background like in your screenshot? Mine is not as good.

Screenshot [http://i.imgur.com/Ry9xt.png](http://i.imgur.com/Ry9xt.png)

---

