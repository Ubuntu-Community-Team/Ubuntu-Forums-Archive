---
title: "Dansguardian blocking innocent google searches"
date: 2009-07-04
forum: Ubuntu Christian Edition
---

### Post by r307a on 2009-07-04
[FONT=Verdana][SIZE=2]Greetings,

This is my first post!

Anyway, I have been using dansguardian for some months now and recently found that even if I search for something as innocent as a drawstring backpack in the "images" section of Google (images.google.com) my search is blocked.  The reason being either [/SIZE][/FONT]**[FONT=Verdana][SIZE=2]"Banned [/SIZE][/FONT]**[FONT=arial,helvetica][COLOR=black][SIZE=4][SIZE=3][COLOR=red][COLOR=black][FONT=Verdana][SIZE=3][FONT=Verdana][SIZE=2]**combination phrase found. Categories: Pornography"** or simply **"Banned phrase found. Categories: Pornography"** when it clearly is not.

I don't want to edit my settings in such a way that will give *every* search in Google (or Google image or Google video) a free pass. 

I've already searched through bannedphraselist and exceptionphraselist in adition to banned/exception url and site lists but could not find images.google.com or "drawstring backpack" within those lists.  I've also already searched throught the relevant blacklists folder and the phraselists folder

I don't know what seems to be the problem. 

Please help.
[/SIZE][/FONT][/SIZE][/FONT][/COLOR][/COLOR][/SIZE][/SIZE][/COLOR][/FONT]

---

### Post by david_kt on 2009-07-05
> **r307a said:**
> [FONT=Verdana][SIZE=2]Greetings,

This is my first post!

Anyway, I have been using dansguardian for some months now and recently found that even if I search for something as innocent as a drawstring backpack in the "images" section of Google (images.google.com) my search is blocked.  The reason being either [/SIZE][/FONT]**[FONT=Verdana][SIZE=2]"Banned [/SIZE][/FONT]**[FONT=arial,helvetica][COLOR=black][SIZE=4][SIZE=3][COLOR=red][COLOR=black][FONT=Verdana][SIZE=3][FONT=Verdana][SIZE=2]**combination phrase found. Categories: Pornography"** or simply **"Banned phrase found. Categories: Pornography"** when it clearly is not.

I don't want to edit my settings in such a way that will give *every* search in Google (or Google image or Google video) a free pass. 

I've already searched through bannedphraselist and exceptionphraselist in adition to banned/exception url and site lists but could not find images.google.com or "drawstring backpack" within those lists.  I've also already searched throught the relevant blacklists folder and the phraselists folder

I don't know what seems to be the problem. 

Please help.
[/SIZE][/FONT][/SIZE][/FONT][/COLOR][/COLOR][/SIZE][/SIZE][/COLOR][/FONT]

You can add that to white list:
gksudo gedit /etc/dansguardian/lists/exceptionphraselist

Add whatwever phrases you want dansguardian to pass.

DK

---

### Post by r307a on 2009-07-05
Thank you for the help but I've also noticed that I'm allowed to go to the site images.google.com but once I type in a search (anything at all) it is blocked using the same reason as before;  " Banned combination phrase found. Categories: Pornography." or " Banned phrase found. Categories: Pornography."[COLOR=black][SIZE=2][FONT=Verdana]

[/FONT][/SIZE][/COLOR][FONT=arial,helvetica][COLOR=black][SIZE=4][SIZE=3][COLOR=red][COLOR=black][FONT=Verdana][SIZE=3][FONT=Verdana][SIZE=2]I was also wondering if someone could explain to me how to create a .Includes list in addition to using the grey list.

Thanks 
[/SIZE][/FONT][/SIZE][/FONT][/COLOR][/COLOR][/SIZE][/SIZE][/COLOR][/FONT]

---

### Post by Dave Doob on 2009-07-07
We use Dansguardian at work to filter the web for our users. The previous IT manager was a Linux lover (and showed me the way :-)) and he installed the software and configured it. I'm the only guy in the IT dept and my Linux knowledge is only basic so when user's Google Images searches recently began to be blocked for the "Banned combination phrase found" reason I was left with the task of trying to find out why.

Using the Dansguardian log file I found that all attempts by users to search on Google Images failed and were blocked due to the phrases "google" and "&safe=off" being detected. To me this rule makes sense as it stops users turning safe search off on Google Images but why is it kicking in even with safe search off. My guess is that Google has made some kind of change to their site but it really is only a guess as I don't have any website knowledge to use to look into this.

I've found the file you can edit to disable this rule but I'm in the same situation as the OP that I want to make sure that Google Images without safe search cannot be accessed so I'm looking for a proper fix. The file is /usr/local/etc/dansguardian/lists/phraselists/pornography/banned and it's the line that contains <google>,<&safe=off> that needs to be disabled. I've not tried this myself yet as everything I do here that affect web access needs to be authorised by non-IT management (fun times!) but as this is affecting our designer's work productivity I guess it's the only way.

The main reason for me posting this is that hopefully some more experienced/knowledgable people might be able to use this information to find the cause. That's if anyone is actually bothered of course :-)


**EDIT**
So I've found that even with the Strict setting used on Google Images, the source still contains the text "&safe=off". I'm guessing this must be new as it would have triggered Dansguardian in the past if it has always been there. 
Again beacause of my lack of web knowledge I'm not sure what part of the site this text in the source refers to. The solutuion is probably right there but it's over my head unfortunately.

Dave

---

### Post by shredkingj on 2009-07-14
We ran across this problem with Dansguardian as well.  The fix is very simple, and disables Dansguardian from matching when Google's safe search is off.  It will still match on weighted phrase matches and other regexes you may have configured.

Edit /etc/dansguardian/lists/phraselists/pornography/banned

Comment out these two lines that has:

<google>,<&safe=off>
<hl=en&safe=off&output=search>

Apparently disabling safe search can still be done.  In that same file, add:

<SafeSearch: Off>

Restart Dansguardian, Google image searches should now work ok.

Check out this link, it also has a solution to a similar problem with Bing: [http://tech.groups.yahoo.com/group/dansguardian/message/22994](http://tech.groups.yahoo.com/group/dansguardian/message/22994)

---

### Post by r307a on 2009-07-16
Thank you,

It works perfectly! ):P

I will most likely add images.google.com to the greysitelist.

Don't know if it makes a difference but I didn't put a space between "SafeSearch:" and "Off" 

Thanks again!

---

### Post by stranger7 on 2009-07-22
> **shredkingj said:**
> We ran across this problem with Dansguardian as well.  The fix is very simple, and disables Dansguardian from matching when Google's safe search is off.  It will still match on weighted phrase matches and other regexes you may have configured.

Edit /etc/dansguardian/lists/phraselists/pornography/banned

Comment out these two lines that has:

<google>,<&safe=off>
<hl=en&safe=off&output=search>

Apparently disabling safe search can still be done.  In that same file, add:

<SafeSearch: Off>

Restart Dansguardian, Google image searches should now work ok.

Check out this link, it also has a solution to a similar problem with Bing: [http://tech.groups.yahoo.com/group/dansguardian/message/22994](http://tech.groups.yahoo.com/group/dansguardian/message/22994)

This solution works for us as well.  Thank you very much for posting it!

---

### Post by fchristophersen on 2009-08-24
Thanks! that worked, but only partially...

Commenting out "<google>,<&safe=off>" and "<hl=en&safe=off&output=search>" allows searches in Google Images with SafeSearch ON without being blocked, but the problem is that now Dansguardian doesn't block searches with SafeSearch OFF!

Adding "<SafeSearch: Off>" or "<SafeSearch:Off>" doesn't fix this.

It's a shame since (as far as i remember), Dansguardian was able to do this in the past. I guess Google has change the way it tags the search results. I hope someone can find a workaround.

---

### Post by fchristophersen on 2009-08-24
I find out what was wrong:

Adding <SafeSearch: Off> does work... but only if you are using Google in english!

Since my language is spanish, i have to add <SafeSearch: Desactivado>

Now the problem is that if an user wants to avoid this block, he could just change Google's interface language!

So i added the translation of "SafeSearch: Off" to many other languages:

<SafeSearch: Aus>
<SafeSearch : Désactivé>
<SafeSearch SafeSearch disattivato>
<Sikkert søk: Av>
<SafeSearch: Desativado>
<&#1041;&#1077;&#1079;&#1086;&#1087;&#1072;&#1089;&#1085;&#1099;&#1081; &#1087;&#1086;&#1080;&#1089;&#1082;: &#1042;&#1099;&#1082;&#1083;>
<&#23433;&#20840;&#25628;&#23563; &#38364;&#38281;>
<&#12475;&#12540;&#12501;&#12469;&#12540;&#12481;: OFF>
<&#1575;&#1604;&#1576;&#1581;&#1579; &#1575;&#1604;&#1570;&#1605;&#1606;: &#1573;&#1610;&#1602;&#1575;&#1601;>
<SafeSearch &#54644;&#51228;>
<Beskyttet søgning: Fra>
<SafeSearch: Ei ole käytössä>
<SafeSearch Uit>
<Filtr SafeSearch: Wy&#322;&#261;czony>
<SafeSearch: Av>
<Güvenli Arama Kapal&#305;>

---

### Post by chog on 2009-11-08
I had this problem also, but only when I did a search in the toolbar search.
I found the problem to be my google settings, but there's a trick. I am in Australia, so I changed the settings for google.com.au but still had problems. A search of the logs showed google.com, not google.com.au. It turns out the google toolbar uses google.com. I had to go to google.com (there's a link on every google.com.* page) and change my settings to SafeSearch On at that site.
Hope that helps.
Chog.

---

