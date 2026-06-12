---
title: "Various observations on MX4 and current OTA"
date: 2015-11-12
forum: Ubuntu Phone and Tablet
---

### Post by andrew-q2 on 2015-11-12
Various thoughts on Mx4 and current OTA.  Please someone let the developers know.

1.I can't answer calls, I can't remember if I have ever answered one.  The phone rings 
and a display at the top of the screen appears with red and green buttons and a grey 
one in the middle.  I assumed you tap green, but this does nothing. Neither do red or 
grey. I could tap one of the dropdown items and a text was sent ok to the caller.  Am I 
missing something obvious?!

2. Battery display.  I don't think it's necessary to show the graph in varying colours 
depending on the charge - around the middle, yellow-ish, it's barely visible.  It's 
being fancy for the sake of it, and in fact detracts.

3. Dekko.  If you delete all items on display, you get a blank screen basically, then 
you tap the open angle bracket, and at least it now shows the folder name.

4. Dekko.  It seems temperamental, I find if I don't use it for a few minutes (but it's 
still invoked) when I next go to it it simply quits.

5. Font size.  I think it's too small in a number of places, perhaps this could be 
generally reviewed. For example, if you tap and hold a link in the browser, the menu 
(open in new tab etc) is in very small chars.  Why not use a bigger font?

6. Font colour (or lack of it). Sometimes it's such a pale grey it's hardly visible. 
For example, the worst case is the File Manager, on the right hand side when it is 
showing files, there are properties shown underneath each name, but the font is so 
close to the grey background, you can't read the details!  Across the apps, there are 
situations where a bolder easier-to-read font could be used.

7. Nederland FM.  It may be unfair to pick on this app, it might be a system thing.  
Having had my ear drums blasted before, the other day I plugged in the earphones and 
turned the volume down before putting them in my ears.  Then I invoked Ned.FM, clicked 
a station, and got blasted; it was now on full volume. Unless I did something silly, 
this is a bug that really need fixing.

8. OSM Touch maps.  The font is far too small and ruins this app.  Even when really 
zoomed in, road names are in a tiny tiny font which is not readable.

9. Keyboard / predictive text.  If you choose one of the suggested words, then carry on 
typing the next word, it doesn't put a space in.  Surely it should?

Lastly, I'd like to try the wifi transfer app, but I don't know how to start an FTP 
client.  If anyone can point me in the right direction, I'd be grateful.  I have my 
laptop with Ubuntu 12.04, and a desktop with Windows 7.  Thanks.

regards,
Andrew

---

### Post by howefield on 2015-11-12
> **andrew-q2 said:**
> Various thoughts on Mx4 and current OTA.  Please someone let the developers know.

This isn't the place to let developers know about your concerns, if you have suggestions or bugs to report then try [here]("https://wiki.ubuntu.com/Touch/GetHelp") and [here]("https://wiki.ubuntu.com/Touch/Bugs").

> 1.I can't answer calls, I can't remember if I have ever answered one.  The phone rings and a display at the top of the screen appears with red and green buttons and a grey one in the middle.  I assumed you tap green, but this does nothing. Neither do red or grey. I could tap one of the dropdown items and a text was sent ok to the caller.  Am I missing something obvious?!

Swipe from the grey button towards the green to accept the call. Swipe grey to red to cancel or drop the call. (Actually I think you can swipe either way, grey to colour, or colour to grey - the point is you need to swipe.) 

> 2. Battery display.  I don't think it's necessary to show the graph in varying colours depending on the charge - around the middle, yellow-ish, it's barely visible.  It's being fancy for the sake of it, and in fact detracts.

File a request for a design change.

> 3. Dekko.  If you delete all items on display, you get a blank screen basically, then you tap the open angle bracket, and at least it now shows the folder name.

4. Dekko.  It seems temperamental, I find if I don't use it for a few minutes (but it's still invoked) when I next go to it it simply quits.

Dekko is still beta software and bugs should be filed.

> 5. Font size.  I think it's too small in a number of places, perhaps this could be generally reviewed. For example, if you tap and hold a link in the browser, the menu (open in new tab etc) is in very small chars.  Why not use a bigger font?

> 6. Font colour (or lack of it). Sometimes it's such a pale grey it's hardly visible. For example, the worst case is the File Manager, on the right hand side when it is showing files, there are properties shown underneath each name, but the font is so close to the grey background, you can't read the details!  Across the apps, there are situations where a bolder easier-to-read font could be used.

7. Nederland FM.  It may be unfair to pick on this app, it might be a system thing.  Having had my ear drums blasted before, the other day I plugged in the earphones and turned the volume down before putting them in my ears.  Then I invoked Ned.FM, clicked a station, and got blasted; it was now on full volume. Unless I did something silly, this is a bug that really need fixing.

File the bugs, you'll be helping.

> 8. OSM Touch maps.  The font is far too small and ruins this app.  Even when really zoomed in, road names are in a tiny tiny font which is not readable.

Get in touch with the developer, details should be in the application description.

> 9. Keyboard / predictive text.  If you choose one of the suggested words, then carry on typing the next word, it doesn't put a space in.  Surely it should?

Does for me and I suspect most others, search launchpad for a similar bug, if you can't find one, file it.

> Lastly, I'd like to try the wifi transfer app, but I don't know how to start an FTP client.  If anyone can point me in the right direction, I'd be grateful.  I have my laptop with Ubuntu 12.04, and a desktop with Windows 7.

Open the WiFiTransfer application and press the "Turn On WifiTransfer" button - if using the File Manager in Ubuntu select the Connect to Server option and type in, eg, [ftp://ubuntu@192.168.1.124:44956](ftp://ubuntu@192.168.1.124:44956) and then the password WiFiTransfer has given you.

Substitute whatever path and information the app gives you in the details section instead of my example above.

You should then be able to transfer files to and from the phones ./local/share/wifitransfer.sil folder. You can use whatever ftp method you like, eg Filezilla as well as the File Manager.

---

### Post by andrew-q2 on 2015-11-13
howefield, thanks for the info and comments.

I was hoping my post could get to the developers somehow, or that they might keep an eye on this forum.  I'm afraid I just don't have time to track down where to post bug reports and do the admin - it would take all evening I should think.

Some specifics:
Taking a call - thanks I see now.  Swiping a grey blob seems to be making it over-complicated.  What's wrong with just tapping a green or red button I wonder?

Spaces between words.  I had auto-correction switched off. Switching it on results in spaces getting put in for you. So I think that's a bug.

WiFi transfer.  Aaagh.  I couldn't get this to work.  Ubuntu 12.04 offered various options, I took "FTP with login".  There was a separate input field for the port so used that.  Wasn't sure if I was to put anything in the location.  Put in ubuntu username and the phone-generated password but just couldn't get it to connect.

Dekko - it's still the case that whilst I can send an email via SMTP, I can't send using my Microsoft Outlook.com email account.  A progress bar gets to 10% then hangs.  Does anyone else get this, please?

Andrew

---

### Post by howefield on 2015-11-14
> **andrew-q2 said:**
> howefield, thanks for the info and comments.

You're most welcome.

> I was hoping my post could get to the developers somehow, or that they might keep an eye on this forum.  I'm afraid I just don't have time to track down where to post bug reports and do the admin - it would take all evening I should think.

That's fine, you are still helping by buying and using the phone even if you do nothing else. There is a also an IRC channel  #ubuntu-touch that you might join if you use IRC, many of the developers can be found in there and are chatty and helpful when time permits.

> Some specifics:
Taking a call - thanks I see now.  Swiping a grey blob seems to be making it over-complicated.  What's wrong with just tapping a green or red button I wonder?

Accidentally accepting or dropping a call I should think eg, the phone is in your bag / pocket and you press a button whilst fumbling to get it.

> Spaces between words.  I had auto-correction switched off. Switching it on results in spaces getting put in for you. So I think that's a bug.

Shrug.

> WiFi transfer.  Aaagh.  I couldn't get this to work.  Ubuntu 12.04 offered various options, I took "FTP with login".  There was a separate input field for the port so used that.  Wasn't sure if I was to put anything in the location.  Put in ubuntu username and the phone-generated password but just couldn't get it to connect.

Can't remember what 12.04 looked like in terms of options ect, but using the File Manger "Connect to Server" option and typing [ftp://ubuntu@192.168.1.124:50638](ftp://ubuntu@192.168.1.124:50638) (as per screenshot) then the password when prompted works perfectly for me. Obviously those are my details, just giving you the syntax. Also Filezilla typing the details into the Quick Connect fields.

> Dekko - it's still the case that whilst I can send an email via SMTP, I can't send using my Microsoft Outlook.com email account.  A progress bar gets to 10% then hangs.  Does anyone else get this, please?

I'll test this out later, but something rings a bell from another thread, I'll try and find it.

---

