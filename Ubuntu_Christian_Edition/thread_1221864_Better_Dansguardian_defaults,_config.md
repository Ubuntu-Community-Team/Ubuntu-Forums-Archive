---
title: "Better Dansguardian defaults, config"
date: 2009-07-24
forum: Ubuntu Christian Edition
---

### Post by Aronzak on 2009-07-24
Dansguardian seems to be mainly oriented as a gateway filter in a network, and has a default installation that is suitable for small children (ie. public libraries etc...). The default setup may not be the best for desktop use. 

In a corporate environment, if there's false positives, the motto is roughly "you don't *need* to be looking at that, even if it is harmless, that so get back to work. More KPIs, drone!". Not so good when someone hits a false positive at home. 

To me, it would be a good idea to raise the default naughtiness level above 50 ("50 is for young children,  100 for old children,  160 for young adults.") Maybe set to ~75 as default, with easy radio button options as well as a slider.

The filetype blocklist is just annoying. The idea with it is to stop users in a Windows network from downloading viruses or tools like ultrasurf (I think there is even an anti malware API for interfacing with ClamAV?). This seems more of an annoyance on the desktop, as there is less benefit. If a user has a sudoer password, DG is very easy to stop, so there's not much point in trying to prevent users from downloading software. Also, viruses are less of an issue (Linux, user responisble for their own computer). At the least, the gansguardian_gui tool should have an option to turn all these off (not editing a file under 'advanced'), or it should be off by default.

It would be good to change the default 'access denied' screen (languages/ukenglish/template.html) . Maybe replace 'YOUR ORG NAME' (line 26) with 'UbuntuCE' or some such? It's also a bit confusing for desktop users to have the phrase 'contact your ICT Coordinator or Network Manager'. What about ' If you have any queries contact your mum or your dad.'? (maybe not like that).

Also, it would be nice to have an option to debug with 'REASONLOGGED' in the html file, as it explicitly shows the score etc... for testing purposes, and/or to have some kind of log viewer (and maybe also a frontend to set up a cron job to email / copy the logs over the network?) Also, the dansguardian_gui script should have mkdir -p to supress the error that the directory also exists, and maybe use gksudo the first time, so users have a familiar password dialog?

One other thing; given a previous thread about innocuous Google searches being blocked, should there be whitelisting of common sites? What about Wikipedia, given that there is useful, neutral information on sexuality, STDs, etc..., and also controvertial stuff like the Virgin Killer cd cover, etc... What do people think?

---

### Post by Caraibes on 2009-07-24
I must say it is the 1st time ever that I am running an internet content filter... I actually run it on my box & my kids' box...I almost uninstalled it various times... Too many false alerts... But I want to learn how to master the tricks.

So far, I had to add some sites in the whitelists, such as Google, Youtube, Google Images etc... 

(google.com
youtube.com
google.com.do
images.google.com.do
ireport.com
terra95.com
shoutcast.com
classic.shoutcast.com)

Same goes for extensions, I had to whitelist .mp3, .iso, .gz, bz2...

I also seem to experiment issues to log into other PCs of my local network via ssh (from the "connect to server" button, in Nautilus)...

Anyway, I still think the project is very good, as there's a need for it... I am a dad... I don't feel like leaving my kids "without brakes" while surfing the net...

---

### Post by Aronzak on 2009-07-24
As to whitelisting wikipedia, this happens:

Access to the page:

[http://en.wikipedia.org/w/index.php?title=In_the_beginning_was_the_Word_Bible_Software&action=edit&section=4](http://en.wikipedia.org/w/index.php?title=In_the_beginning_was_the_Word_Bible_Software&action=edit&section=4)

... has been denied for the following reason:

Banned Regular Expression URL found.

Categories:

Banned Regular Expression URLs

What an annoyance.

---

### Post by david_kt on 2009-07-25
> **Aronzak said:**
> 
To me, it would be a good idea to raise the default naughtiness level above 50 ("50 is for young children,  100 for old children,  160 for young adults.") Maybe set to ~75 as default, with easy radio button options as well as a slider.

I have put a slider to choose between 50 to 160, it is easy also to make the default to 75 if most of people here agree. As for radio button, it was easy as wel to add, but may be make the menu more cluttered as the slider could fulfill the need better, I guess. 

> **Aronzak said:**
> 
The filetype blocklist is just annoying. The idea with it is to stop users in a Windows network from downloading viruses or tools like ultrasurf (I think there is even an anti malware API for interfacing with ClamAV?). This seems more of an annoyance on the desktop, as there is less benefit. If a user has a sudoer password, DG is very easy to stop, so there's not much point in trying to prevent users from downloading software. Also, viruses are less of an issue (Linux, user responisble for their own computer). At the least, the gansguardian_gui tool should have an option to turn all these off (not editing a file under 'advanced'), or it should be off by default.

Good feedback, except for 

" If a user has a sudoer password, DG is very easy to stop,...."

This DG is for your kids, not for you. If you are using the computer, it is better to stop dansguardian as you are not kids anymore I guess ..... Actually I don't even use DG, I just try to make easy for people having kids.

It is true the default setting of DG, and any other similar software, would be very restrictive. It is to have total control of the filtering system:

"You allow what you approve, and none should go without your approval"

> **Aronzak said:**
> 
It would be good to change the default 'access denied' screen (languages/ukenglish/template.html) . Maybe replace 'YOUR ORG NAME' (line 26) with 'UbuntuCE' or some such? It's also a bit confusing for desktop users to have the phrase 'contact your ICT Coordinator or Network Manager'. What about ' If you have any queries contact your mum or your dad.'? (maybe not like that).

True, it is just I do not have time yet to figure out how to do that. I want to avoid overriding files, but editing the file instead. I will surely come to that later.


> **Aronzak said:**
> 
Also, it would be nice to have an option to debug with 'REASONLOGGED' in the html file, as it explicitly shows the score etc... for testing purposes, and/or to have some kind of log viewer (and maybe also a frontend to set up a cron job to email / copy the logs over the network?)

Good idea, I will think of a way to do that.


> **Aronzak said:**
> 
 Also, the dansguardian_gui script should have mkdir -p to supress the error that the directory also exists,

This has been removed. Before I am using temporary file and need to make sure there is .cache folder just in case it was deleted by user. But if you have updated to lates dansguardian gui, there is no more temporary files and no more mkdir.

> **Aronzak said:**
> 
 and maybe use gksudo the first time, so users have a familiar password dialog?

That what I have tested before, but some of the command would not work with gksudo, so, I have to use sudo instead.


> **Aronzak said:**
> 
One other thing; given a previous thread about innocuous Google searches being blocked, should there be whitelisting of common sites? What about Wikipedia, given that there is useful, neutral information on sexuality, STDs, etc..., and also controvertial stuff like the Virgin Killer cd cover, etc... What do people think?

Well, I would like to hear the comments from user as well. If that is false positive, then we should try to improve it. But for google images, that is a valid reason behind: 

"safe search is off"

You should insist your kids to on safe search, to avoid inappropriate images. As dansguardian could not check the content if images!

Thank you for your feedback.
DK

---

### Post by david_kt on 2009-07-25
> **Caraibes said:**
> I must say it is the 1st time ever that I am running an internet content filter... I actually run it on my box & my kids' box...I almost uninstalled it various times... Too many false alerts... But I want to learn how to master the tricks.

So far, I had to add some sites in the whitelists, such as Google, Youtube, Google Images etc... 

(google.com
youtube.com
google.com.do
images.google.com.do
ireport.com
terra95.com
shoutcast.com
classic.shoutcast.com)

Same goes for extensions, I had to whitelist .mp3, .iso, .gz, bz2...

I also seem to experiment issues to log into other PCs of my local network via ssh (from the "connect to server" button, in Nautilus)...


Instead of whitelisting, you could remove it from blacklist. Just put # in front of the things you want to allow. That would be much easier.

Whitelist is for false positive actually, not for removing blacklist. Please let me know if you need further instruction on this.

DK

---

### Post by Aronzak on 2009-08-10
> **david_kt said:**
> I have put a slider to choose between 50 to 160, it is easy also to make the default to 75 if most of people here agree. As for radio button, it was easy as wel to add, but may be make the menu more cluttered as the slider could fulfill the need better, I guess.

OK, I've put together a small script with two zenity commands, with the option in a list to use a slider:

```
output=$(zenity --title="Select filter level" --text="Please choose one of the filtering levels, or choose a custom level." --list --column="Levels:" "50: for young children" "100: for old children" "160: for young adults" "Custom" --height=230)

if [ "$output" = "Custom" ]; then
    FILTER_LEVEL=$(zenity --title="Slide to choose filter level" --scale --text "Strict                                     Less Strict" --max-value=160)
    #FILTER_LEVEL=$(zenity --title="Slide to choose filter level" --scale --text "Strict                                     Less Strict" --min-value=50 --max-value=160 --value="$FILTER_LEVEL")
else
    FILTER_LEVEL="`echo $output | grep -o ^[^:]*`"
fi

echo "$FILTER_LEVEL"

```The first one in the block has the 'min-value' setting removed, as it didn't work to test. You will want to use the second one.

Not an ideal solution, with two window boxes, but good enough.

As to HTML; here's a version of the table in template.html:

```
<tr>
    <td align=center valign=bottom width=150 bgcolor=#B0C4DE>
    <font face=arial,helvetica size=1 color=black>
    UbuntuCE
    </td>
    <td width=550 bgcolor=#FFFFFF align=center valign=center>
    <font face=arial,helvetica color=black>
    <font size=4>
    Access to the page:
    <br><br>
    <a href="-URL-" target="_blank">-URL-</a>
    <br><br>
    <font size=3>
    ... has been denied for the following reason:
    <br><br>
    <font color=red>
    <b>-REASONGIVEN-</b>
    <font color=black>
    <br><br>
    Categories:
    <br><br>
    <font color=red>
    <b>-CATEGORIES-</b>
    <font color=black>
    <br><br>
    Full Reason (debug/configure):
    <textarea>-REASONLOGGED-</textarea>   
    <br><br><br><br>
    You are seeing this error because what you attempted to access appears to contain,
    or is labeled as containing, material that has been deemed inappropriate.
    <br><br>
    If you have issues with false positives, please request the system administrator to whitelist the domain.
    <br><br><br><br>
    <font size=1>
    Powered by <a href="http://www.dansguardian.org" target="_blank">DansGuardian</a>
    </td>
</tr>
```The main differences are 'UbuntuCE' replaces YOUR ORG NAME, and a slightly less ambiguous notice to request the whitelisting of domains with false positives.

Also, this has the -REASONLOGGED- full explanation in a small text box, which is useful in showing the exact number that the weighted phrases come out, which can help in fine tuning the filter. I was thinking have a version with this as /etc/dansguardian/languages/ukenglish/extended.html and /etc/dansguardian/languages/ukenglish/basic.html, with /etc/dansguardian/languages/ukenglish/template.html as a symbolic link that can change depending on the setting in dansguardian_gui.

Thanks for your responsiveness to feedback David. I'll have a look at this some more over the next few months when I'm not busy.

---

### Post by david_kt on 2009-08-11
Thank you for your feedback. I will take a look after I release the server version.
For the custom level, it did not work with minimum value because you set contradicting value:

Minimum is 50, but default value is 0.

That is why it would not work. But if we put that script in main program, it would work as the default value will never get to 0 unless it is edited manually.

DK

---

