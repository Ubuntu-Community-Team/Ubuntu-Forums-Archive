---
title: "can someone please copy and paste the text from just one webpage here (work blockage)"
date: 2009-10-29
forum: The Cafe
---

### Post by hanzj on 2009-10-29
Hello,
I am at a computer which blocks lifehacker.com, but I need to access a webpage to make me more productive at work.
Could someone please copy and paste (or screenshot; or save as pdf; or save as html) the ff: URL:
 
 
[lifehacker.com/software/texter/lifehacker-code-texter-windows-238306.php]("http://lifehacker.com/software/texter/lifehacker-code-texter-windows-238306.php")
 
Than kyou.

---

### Post by Maheriano on 2009-10-29
This?

> Windows only: Text substitution app Texter saves you countless keystrokes by replacing abbreviations with commonly used phrases you define.



Unlike software-specific text replacement features, Texter runs in the Windows system tray and works in any application you're typing in. Texter can also set return-to markers for your cursor and insert clipboard contents into your replacement text, in addition to more advanced keyboard macros. Did we mention it's free?

Hit the jump for a a quick video demonstration, a full feature rundown with screenshots, and the download link.

Since it's always easier to show than tell, the following video demonstrates how to use Texter's basic features:

---

### Post by hanzj on 2009-10-29
yes, could you paste the entire page? I'm specifically looking for the "advanced" section.

---

### Post by albandy on 2009-10-29
zip file attached

---

### Post by hanzj on 2009-10-29
thanks, albandy.

---

### Post by Xbehave on 2009-10-29
Windows only: Text substitution app Texter saves you countless keystrokes by replacing abbreviations with commonly used phrases you define.

texter%20medium.png

Unlike software-specific text replacement features, Texter runs in the Windows system tray and works in any application you're typing in. Texter can also set return-to markers for your cursor and insert clipboard contents into your replacement text, in addition to more advanced keyboard macros. Did we mention it's free?

Hit the jump for a a quick video demonstration, a full feature rundown with screenshots, and the download link.

Since it's always easier to show than tell, the following video demonstrates how to use Texter's basic features:

Check out more ways text substitution can make you more productive.
Texter

Version: 0.6
Last updated: November 6, 2007
Author: Adam Pash
License: GNU Public License

What it does: Lets you define text substitution hotstrings that, when triggered, will replace hotstring with a larger piece of text. By entering your most commonly-typed snippets of text into Texter, you can save countless keystrokes in the course of the day.

One common use example given for applications like Texter is email signatures. For example, you could define a series of hotstrings that would be replaced by different signatures. So something like sig1 will automatically be replaced by your full signature when triggered.
Basic Use

As you can see from the video, there are a lot of ways that you can use Texter. Signatures, addresses, and commonly used abbreviations can be quickly and easily expanded from very small user-defined snippets.

Add new hotstrings: You can add a new replacement on-the-fly by hitting Ctrl-Shift-H, typing in your hotstring and the replacement text, selecting the trigger you want to execute the replacement (Enter, Tab, and/or Space), and hitting OK. For example, in the video above I typed sig1 and then pressed Tab to execute the replacement.

Manage replacement text: You can edit your replacements at any time through the Manage hotstrings option in the system tray menu (or you can assign a keyboard shortcut through the Preferences - the shortcut is empty by default, but I use Ctrl-Shift-M to manage hotstrings).

You can also insert the clipboard contents into your replacement text by using the %c operator. The other special bit of text is %|, which lets you designate a place you'd like the cursor to return to after the text is replaced. I use this all the time with HTML tags I've scripted with Texter. For example:

(For some reason this video and the one below are sticking - just give YouTube's progress bar a little nudge.)

    <a href="%c">%|</a>

If I've copied a URL to my clipboard, this replacement will paste the URL in the appropriate spot and place the cursor inside the anchor tag. This replacement alone (which I trigger by typing hre then hitting Tab) saves me countless keystrokes everyday and saves me the trouble of worrying that I may have forgotten to close a tag when I'm working on Lifehacker.

Texter's other built-in variables are:

    * %ds: Short date, which will return the date in the following format: 3/9/2007.
    * %dl: Long date, which returns the date in the following format: Friday, March 09, 2007.
    * %t: Time, which returns the time as follows: 1:30 PM.


Advanced Use

In addition to basic text replacement described above, Texter also lets you perform more advanced scripting commands using keyboard shortcuts by selecting Script from the drop-down box. Again, to demonstrate, check out the video of how I use Texter to send personalized email replies in a few short keystrokes.

The whole process happen may happen a little too quickly in the video for you to see what's happening, but I've scripted an action into Texter that sends the keystrokes necessary to copy the name of the email's sender, then paste the name into my personalized email reply. The text of that replacement is:

    +{Tab}^{Home}^+{Right}^c{Tab}{BS}Thanks for the email, ^v{BS}.

There's a lot going on there, but it's actually much more simple than it may seem at first glance. Modifier keys like Alt, Control, and Shift are represented by special characters. They are:
Special Characters in Texter Script mode Texter special character 	Keyboard equivalent
# 	Windows key
! 	Alt key
^ 	Control key
+ 	Shift key

So in the example above, ^c is the same as Ctrl-C (copy).

You can also send literal keys, like Tab, Enter, Up, Down, Left, Right, and Backspace, just by wrapping them in curly brackets. For example, {Tab} will send a literal Tab. By extension, +{Tab} will send Shift-Tab, a combination that will move backwards in a form (which I use in the email example above). To send the literal forms of the special characters above, just wrap them in the same curly brackets.

I mostly use this function to send personal replies to Lifehacker email, but it can also come in handy for filling in some forms (if you know what the layout will be). With the scripting feature, your imagination's the limit, and I'd love to hear how others might use it.
Installation

There are several ways you can install Texter. The easiest is to download and run the installer below:

Texter Installer

However, Texter is also portable, so if you want to take it with you on your portable drive, you can grab the texter.exe executable.

Texter Executable

Finally, Texter is open source, written using AutoHotkey, so if you're an AutoHotkey user and you want to check out or run Texter from the source, grab the source code.

Texter Source Code

To use the installer, just run the executable and point Texter to the folder you'd like to install it to (defaults to Program Files\Texter). You can also check out the latest and greatest Texter source code from the Texter repository.

System Requirements: Texter is Windows only. It's been tested it on Windows XP, and all reports so far have been positive. That's not to say Texter is without flaw - you are our guinea pigs on this one.

Known issues: Release 0.2 should take care of most, if not all, compatibility issues. If you're having trouble, be sure Texter is set to Compatibility mode (through the Preferences).

Changelog:

    * Version 0.6: Lots of redesigned code, can now rename existing hotstrings, universal autocorrect, instant replacements added and more.
    * Version 0.5: Bundles, extensive code optimization by Dustin Luck, punctuation in hotstrings, other minor improvements.
    * Version 0.4: Prompts, delays, disable via right-click, Synergy compatibility, other bug fixes and minor feature improvements.
    * Version 0.3: Printable lists, update check, improved execution (i.e., better at detecting hotstrings in different situations), compatibility with more programs, various code enhancements, new icon and other visual enhancements.
    * Version 0.2: Fixed major incompatibility issues (added Compatibility and Clipboard modes), added option to run at startup, double-clicking the system tray icon launches the script management, and a bundle of other optimizations, features, and fixes. For a closer look, check out the more extensive-but-incomplete features and fixes for this release.
    * Version 0.1: Released.

Bug reports and feature requests: Leave a comment here if you've got any feature requests or bug reports for Texter. Newcomers, here's how to get a comment login. — Adam Pash
Download Texter


Send an email to Adam Pash, the author of this post, at [email]adam@lifehacker.com[/email].

---

