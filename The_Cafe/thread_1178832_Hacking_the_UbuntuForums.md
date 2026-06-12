---
title: "Hacking the UbuntuForums"
date: 2009-06-04
forum: The Cafe
---

### Post by monsterstack on 2009-06-04
Anyone tried to fiddle with the Ubuntu Forums with GreaseMonkey? I'm trying out a few scripts I found [here]("http://userscripts.org/scripts/show/46049") [userscripts.org]. Have a look at the screenshots. Does anyone have any other GreaseMonkey hacks for changing the way the forum looks?

---

### Post by Vostrocity on 2009-06-04
Ooh very nice, I was wondering when someone would make some Stylish styles for Ubuntu Forums, but Userscripts work too. Matches very well with my theme.

---

### Post by lovinglinux on 2009-06-05
I have a very simple Stylish script to dim the page. Good for the eyes.

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("ubuntuforums.org"){

body{
background:#333 !important;
opacity:.9 !important;
}
```

---

### Post by DeadSuperHero on 2009-06-05
This thread is not living up to the title. I am sorely disappointed that you meant the RMS version of "Hacking", instead of the commonplace hacking done anymore.

Oh well. No admin panel for me.

---

### Post by lovinglinux on 2009-06-05
> **Vostrocity said:**
> Ooh very nice, I was wondering when someone would make some Stylish styles for Ubuntu Forums, but Userscripts work too. Matches very well with my theme.

The exact same script for Stylish can be obtained [here](http://userstyles.org/styles/16677).

---

### Post by LookTJ on 2009-06-05
> **Mr. Psychopath said:**
> This thread is not living up to the title. I am sorely disappointed that you meant the RMS version of "Hacking", instead of the commonplace hacking done anymore.

Oh well. No admin panel for me.
What do you mean? black-hat(bad) or white-hat(good)?

There's also grey-hat(questionable)

But I think the title meant "hacking" in the sense of a white-hat.

---

### Post by Dark Aspect on 2009-06-05
How do I use these scripts?

---

### Post by LookTJ on 2009-06-05
I gave up on customizing looks on websites long time ago.  I used both, and liked Stylish best.

---

### Post by monsterstack on 2009-06-05
> **Dark Aspect said:**
> How do I use these scripts?

Install the [Greasemonkey plugin]("https://addons.mozilla.org/en-US/firefox/addon/748") [mozilla.org] for Firefox. Then navigate to the link in my original post and click the "Install" button on that page. Greasemonkey can be used for much more than just fiddling with how a site looks. There are tonnes of scripts at the site I linked to.

---

### Post by Dark Aspect on 2009-06-05
> **monsterstack said:**
> Install the [Greasemonkey plugin]("https://addons.mozilla.org/en-US/firefox/addon/748") [mozilla.org] for Firefox. Then navigate to the link in my original post and click the "Install" button on that page. Greasemonkey can be used for much more than just fiddling with how a site looks. There are tonnes of scripts at the site I linked to.

Thank you

---

### Post by monsterstack on 2009-06-05
> **lovinglinux said:**
> The exact same script for Stylish can be obtained [here](http://userstyles.org/styles/16677).

I didn't know about Stylish. Thanks for the link. I'm using it now with the blue Ubuntuforums theme. Very cool stuff.

---

### Post by CJ Master on 2009-06-05
> **Taylor said:**
> What do you mean? black-hat(bad) or white-hat(good)?

There's also grey-hat(questionable)

But I think the title meant "hacking" in the sense of a white-hat.

Erm, it's none. Hacking generally involves hacking. This is just changing client-side appearance.

---

### Post by ghindo on 2009-06-05
> **Mr. Psychopath said:**
> This thread is not living up to the title. I am sorely disappointed that you meant the RMS version of "Hacking", instead of the commonplace hacking done anymore.

Oh well. No admin panel for me.Hacking is an incredibly broad term.

---

### Post by monsterstack on 2009-06-05
> **CJ Master said:**
> Erm, it's none. Hacking generally involves hacking. This is just changing client-side appearance.

It can be called hacking if you actually write the code yourself. Just using a script somebody else made only makes you a script kiddie. But "Skiddy Ubuntu Forums"  hardly makes for an alluring thread title.

---

### Post by JK3mp on 2009-06-05
Who cares, if you get what he meant, and its not INCREDIBLY disturbing to you, why bother it. Greasemonkey is fun to mess around with every so often, i use it for custom looks in my GMAIL box.

---

### Post by TheNosh on 2009-06-05
is there a way to do this in opera?

---

### Post by monsterstack on 2009-06-05
> **TheNosh said:**
> is there a way to do this in opera?

Yeah. Save the Greasemonkey scripts in a folder somewhere on your computer, then go to Opera's Tools>Preferences>Advanced>Content>Javascript Options, and choose the folder you saved the scripts in. Then go and do your browsing. Works for me.

---

### Post by TheNosh on 2009-06-05
thank you. i'll try that out in a bit

---

### Post by lovinglinux on 2009-06-05
> **monsterstack said:**
> Install the [Greasemonkey plugin]("https://addons.mozilla.org/en-US/firefox/addon/748") [mozilla.org] for Firefox. Then navigate to the link in my original post and click the "Install" button on that page. Greasemonkey can be used for much more than just fiddling with how a site looks. There are tonnes of scripts at the site I linked to.

After installing greasemonkey you can add [this script](http://userscripts.org/scripts/show/41722), that add options to view YouTube videos with mplayer :)

You can also install [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108) to change styles on web sites or Firefox. For example, [this style](http://userstyles.org/styles/10) merges the "reload" and "stop" buttons of Firefox into a single button, that changes dynamically.

I have modified the Dark theme style to make it blend with [Chromifox theme](https://addons.mozilla.org/en-US/firefox/addon/8782). Get the code below (improvements are welcome):

```
/****UbuntuForums.org Chromifox Part 1****/
/****Chromifox colors by: lovinglinux ****/

/****Original Script****/
/****UbuntuForums.org Dark part 1****/
/****Created by: tjwoosta ****/

@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain("ubuntuforums.org") {

body {background-image:none !important; background-color:#DFEAF8 !important; }

.tborder {border:0px !important;}

span.forumhome_stats {border:none !important;}

.page, .vbclean_topfg, .vbclean_top *, .vbclean_bottom *, .alt1, .alt2, .tborder, .alt1Active, .pagebody, .tcat, .vbmenu_control, .ubuntu_quotebackground, .panelsurround, .panel, .vbclean_bottomfg, .tfoot, .forumhome_stats, .vbclean_postbitmsgfg, .vbclean_postbitmsg *, .vBulletin_editor {background-color: #8DAFD8 !important;}
.vbclean_bottom *, .vbclean_top *, .vbclean_postbitmsg * {border-left: 1px solid #8DAFD8 !important; border-right: 1px solid #8DAFD8!important;}

.alt1 {border-bottom:0 !important; border-right:0 !important;}
.vbclean_postbitmsgfg .tborder tbody td {border-right:0 !important;}

.alt3 {background-color: #F2F7FD !important;}

.vbclean_noticefg, .vbclean_notice *, .vbclean_notice1 *, .vbclean_notice2 *, .vbclean_notice3 *, .vbclean_notice4 *, .vbclean_notice5 * {background-color:#5199EE !important;}
.vbclean_noticefg, .vbclean_notice *, .vbclean_notice1 *, .vbclean_notice2 *, .vbclean_notice3 *, .vbclean_notice4 *, .vbclean_notice5 * {border-right:1px solid #5199EE !important; border-left:1px solid #FF000A !important;}

.vbclean_announcefg, .vbclean_announce *, .vbclean_announce1 *, .vbclean_announce2 *, .vbclean_announce3, .vbclean_announce4, .vbclean_announce5 {background-color:#5596F2 !important;}
.vbclean_announcefg, .vbclean_announce *, .vbclean_announce1, .vbclean_announce2, .vbclean_announce3, .vbclean_announce4, .vbclean_announce5 {border-right:1px solid #5596F2 !important; border-left:1px solid #5596F2 !important;}

.vbclean_stickyfg, .vbclean_sticky *, .vbclean_sticky1, .vbclean_sticky2, .vbclean_sticky3, .vbclean_sticky4, .vbclean_sticky5 {background-color:#5596F2 !important;}
.vbclean_stickyfg, .vbclean_sticky *, .vbclean_sticky1, .vbclean_sticky2, .vbclean_sticky3, .vbclean_sticky4, .vbclean_sticky5 {border-right:1px solid #5596F2 !important; border-left:1px solid #5596F2 !important;}

.vbclean_postbitlegfg, .vbclean_postbitleg *, .alt4 {background-color:#DFEAF8 !important;}
.vbclean_postbitleg * {border-right:1px solid #DFEAF8 !important; border-left:1px solid #DFEAF8 !important;}

.vbclean_forumdescfg, .vbclean_forumdesc * {background-color:#5596F2 !important;}
.vbclean_forumdesc * {border-right: 1px solid #5596F2 !important; border-left: 1px solid #5596F2 !important;}

.vbclean_postbitlegfg .alt4 {border-bottom:2px solid #DFEAF8 !important;}
.vbclean_postbitlegfg .alt3 {border-right:2px solid #DFEAF8 !important;}
.forumhome_stats {border: 1px solid #DFEAF8 !important;}

.vbclean_navbar_bg, .vblcean_navbar *, .vbclean_newthreadfg, .vbclean_newthread * {background-color:#5596F2 !important;}
.vblcean_navbar *, .vbclean_newthread *  {border-right: 1px solid #5596F2 !important;border-left: 1px solid #5596F2 !important;}

.tcat {border-bottom: 1px solid #DFEAF8 !important;}

.thead, .vbclean_fhomecatfg, .vbclean_fhomecat *, .vbclean_fhomecatfg .forumhome_stats {background-color: #5596F2 !important;} 
.vbclean_fhomecat * {border-right: 1px solid #5596F2 !important;border-left: 1px solid #5596F2 !important;}

.ubuntu_quotebackground {border:solid #5596F2 !important; border-width: 1px 1px 1px 7px !important;}

.thead {border-bottom:2px solid #5596F2 !important;}

.vbclean_fhomecat_topfg, .vbclean_fhomecat_top *, .vbclean_fhomecat_topfg .forumhome_stats {background-color:#5596F2 !important;}
.vbclean_fhomecat_top * {border-right:1px solid #5596F2 !important; border-left:1px solid #5596F2 !important;}

#navbar, .pda, .posttop {background-color:#5596F2 !important;}
.posttext {background-color:#5596F2 !important;}
.post {border:1px solid #5596F2 !important;}

.popup_feedback, .alt_pickbutton, .popup_pickbutton, .imagebutton, .inlineimg {background-color:#8DAFD8 !important;}

.fieldset * {background-color:#8DAFD8 !important;}
.fieldset {border: none !important;}

.bginput * {background-color:#DFEAF8 !important;}
.bginput {background-color:#DFEAF8 !important;}

#vB_Editor_001_textarea, #vB_Editor_QR_textarea {background-color:#B8C1CC !important;}

#collapseobj_forumhome_lastpostby_302, #collapseobj_forumhome_lastpostby_211, #collapseobj_forumhome_lastpostby_133, #collapseobj_forumhome_lastpostby_132, #collapseobj_forumhome_lastpostby_223, #collapseobj_forumhome_lastpostby_131, #collapseobj_forumhome_lastpostby_135, #collapseobj_forumhome_lastpostby_140, #collapseobj_forumhome_lastpostby_138, #collapseobj_forumhome_lastpostby_254, #collapseobj_forumhome_lastpostby_136, #collapseobj_forumhome_lastpostby_323, #collapseobj_forumhome_lastpostby_322, #collapseobj_forumhome_lastpostby_7, #collapseobj_forumhome_lastpostby_146, #collapseobj_forumhome_lastpostby_158, #collapseobj_forumhome_lastpostby_256, #collapseobj_forumhome_lastpostby_134, #collapseobj_forumhome_lastpostby_244 {background: #DFEAF8 !important; border: none !important;}

.stickybg {background-color:#DFEAF8 !important;}


/**TEXT**/
* {color:#333333 !important;}
.smallfont span, *:link {color:#170A4F !important;}

/**INPUT BOXES**/
 input , select, button {background: #B8C1CC !important; color: #8a8a8a !important;  border-color: #B8C1CC !important;}

}
```

---

### Post by Johnsie on 2009-06-05
Awww... so nobody actually changed it to the Ubumtu forums?

Ubumtu - Linux for bums with no jobs who can't afford Windows.


Please don't take that phrase seriously.

---

### Post by HappinessNow on 2009-06-05
> **monsterstack said:**
> Anyone tried to fiddle with the Ubuntu Forums with GreaseMonkey? I'm trying out a few scripts I found [here]("http://userscripts.org/scripts/show/46049") [userscripts.org]. Have a look at the screenshots. Does anyone have any other GreaseMonkey hacks for changing the way the forum looks?

Thanks for the Hack!!!!

I have always dislike the boring bland default colors of ubuntuforums...the brightness is very hard on the eyes!

---

### Post by monsterstack on 2009-06-05
> **lovinglinux said:**
> After installing greasemonkey you can add [this script](http://userscripts.org/scripts/show/41722), that add options to view YouTube videos with mplayer :)

You can also install [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108) to change styles on web sites or Firefox. For example, [this style](http://userstyles.org/styles/10) merges the "reload" and "stop" buttons of Firefox into a single button, that changes dynamically.

I have modified the Dark theme style to make it blend with [Chromifox theme](https://addons.mozilla.org/en-US/firefox/addon/8782). Get the code below (improvements are welcome):

```
/****UbuntuForums.org Chromifox Part 1****/
/****Chromifox colors by: lofinglinux ****/

/****Original Script****/
/****UbuntuForums.org Dark part 1****/
/****Created by: tjwoosta ****/

@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain("ubuntuforums.org") {

body {background-image:none !important; background-color:#DFEAF8 !important; }

.tborder {border:0px !important;}

span.forumhome_stats {border:none !important;}

.page, .vbclean_topfg, .vbclean_top *, .vbclean_bottom *, .alt1, .alt2, .tborder, .alt1Active, .pagebody, .tcat, .vbmenu_control, .ubuntu_quotebackground, .panelsurround, .panel, .vbclean_bottomfg, .tfoot, .forumhome_stats, .vbclean_postbitmsgfg, .vbclean_postbitmsg *, .vBulletin_editor {background-color: #8DAFD8 !important;}
.vbclean_bottom *, .vbclean_top *, .vbclean_postbitmsg * {border-left: 1px solid #8DAFD8 !important; border-right: 1px solid #8DAFD8!important;}

.alt1 {border-bottom:0 !important; border-right:0 !important;}
.vbclean_postbitmsgfg .tborder tbody td {border-right:0 !important;}

.alt3 {background-color: #F2F7FD !important;}

.vbclean_noticefg, .vbclean_notice *, .vbclean_notice1 *, .vbclean_notice2 *, .vbclean_notice3 *, .vbclean_notice4 *, .vbclean_notice5 * {background-color:#5199EE !important;}
.vbclean_noticefg, .vbclean_notice *, .vbclean_notice1 *, .vbclean_notice2 *, .vbclean_notice3 *, .vbclean_notice4 *, .vbclean_notice5 * {border-right:1px solid #5199EE !important; border-left:1px solid #FF000A !important;}

.vbclean_announcefg, .vbclean_announce *, .vbclean_announce1 *, .vbclean_announce2 *, .vbclean_announce3, .vbclean_announce4, .vbclean_announce5 {background-color:#5596F2 !important;}
.vbclean_announcefg, .vbclean_announce *, .vbclean_announce1, .vbclean_announce2, .vbclean_announce3, .vbclean_announce4, .vbclean_announce5 {border-right:1px solid #5596F2 !important; border-left:1px solid #5596F2 !important;}

.vbclean_stickyfg, .vbclean_sticky *, .vbclean_sticky1, .vbclean_sticky2, .vbclean_sticky3, .vbclean_sticky4, .vbclean_sticky5 {background-color:#5596F2 !important;}
.vbclean_stickyfg, .vbclean_sticky *, .vbclean_sticky1, .vbclean_sticky2, .vbclean_sticky3, .vbclean_sticky4, .vbclean_sticky5 {border-right:1px solid #5596F2 !important; border-left:1px solid #5596F2 !important;}

.vbclean_postbitlegfg, .vbclean_postbitleg *, .alt4 {background-color:#DFEAF8 !important;}
.vbclean_postbitleg * {border-right:1px solid #DFEAF8 !important; border-left:1px solid #DFEAF8 !important;}

.vbclean_forumdescfg, .vbclean_forumdesc * {background-color:#5596F2 !important;}
.vbclean_forumdesc * {border-right: 1px solid #5596F2 !important; border-left: 1px solid #5596F2 !important;}

.vbclean_postbitlegfg .alt4 {border-bottom:2px solid #DFEAF8 !important;}
.vbclean_postbitlegfg .alt3 {border-right:2px solid #DFEAF8 !important;}
.forumhome_stats {border: 1px solid #DFEAF8 !important;}

.vbclean_navbar_bg, .vblcean_navbar *, .vbclean_newthreadfg, .vbclean_newthread * {background-color:#5596F2 !important;}
.vblcean_navbar *, .vbclean_newthread *  {border-right: 1px solid #5596F2 !important;border-left: 1px solid #5596F2 !important;}

.tcat {border-bottom: 1px solid #DFEAF8 !important;}

.thead, .vbclean_fhomecatfg, .vbclean_fhomecat *, .vbclean_fhomecatfg .forumhome_stats {background-color: #5596F2 !important;} 
.vbclean_fhomecat * {border-right: 1px solid #5596F2 !important;border-left: 1px solid #5596F2 !important;}

.ubuntu_quotebackground {border:solid #5596F2 !important; border-width: 1px 1px 1px 7px !important;}

.thead {border-bottom:2px solid #5596F2 !important;}

.vbclean_fhomecat_topfg, .vbclean_fhomecat_top *, .vbclean_fhomecat_topfg .forumhome_stats {background-color:#5596F2 !important;}
.vbclean_fhomecat_top * {border-right:1px solid #5596F2 !important; border-left:1px solid #5596F2 !important;}

#navbar, .pda, .posttop {background-color:#5596F2 !important;}
.posttext {background-color:#5596F2 !important;}
.post {border:1px solid #5596F2 !important;}

.popup_feedback, .alt_pickbutton, .popup_pickbutton, .imagebutton, .inlineimg {background-color:#8DAFD8 !important;}

.fieldset * {background-color:#8DAFD8 !important;}
.fieldset {border: none !important;}

.bginput * {background-color:#DFEAF8 !important;}
.bginput {background-color:#DFEAF8 !important;}

#vB_Editor_001_textarea, #vB_Editor_QR_textarea {background-color:#B8C1CC !important;}

#collapseobj_forumhome_lastpostby_302, #collapseobj_forumhome_lastpostby_211, #collapseobj_forumhome_lastpostby_133, #collapseobj_forumhome_lastpostby_132, #collapseobj_forumhome_lastpostby_223, #collapseobj_forumhome_lastpostby_131, #collapseobj_forumhome_lastpostby_135, #collapseobj_forumhome_lastpostby_140, #collapseobj_forumhome_lastpostby_138, #collapseobj_forumhome_lastpostby_254, #collapseobj_forumhome_lastpostby_136, #collapseobj_forumhome_lastpostby_323, #collapseobj_forumhome_lastpostby_322, #collapseobj_forumhome_lastpostby_7, #collapseobj_forumhome_lastpostby_146, #collapseobj_forumhome_lastpostby_158, #collapseobj_forumhome_lastpostby_256, #collapseobj_forumhome_lastpostby_134, #collapseobj_forumhome_lastpostby_244 {background: #DFEAF8 !important; border: none !important;}

.stickybg {background-color:#DFEAF8 !important;}


/**TEXT**/
* {color:#333333 !important;}
.smallfont span, *:link {color:#170A4F !important;}

/**INPUT BOXES**/
 input , select, button {background: #B8C1CC !important; color: #8a8a8a !important;  border-color: #B8C1CC !important;}

}
```

Very pretty-looking. Thanks for sharing :)

---

### Post by billgoldberg on 2009-06-05
> **monsterstack said:**
> Anyone tried to fiddle with the Ubuntu Forums with GreaseMonkey? I'm trying out a few scripts I found [here]("http://userscripts.org/scripts/show/46049") [userscripts.org]. Have a look at the screenshots. Does anyone have any other GreaseMonkey hacks for changing the way the forum looks?

I wouldn't call that hacking.

---

### Post by monsterstack on 2009-06-05
> **billgoldberg said:**
> I wouldn't call that hacking.

Come on, man, read the thread. We've been over this one already.

---

### Post by fatality_uk on 2009-06-05
> **monsterstack said:**
> Come on, man, read the thread. We've been over this one already.

Ahh ok.

---

### Post by ibuclaw on 2009-06-05
> 
Hack has several related meanings in the technology and computer science fields. It may refer to a clever or quick fix to a computer program problem, or to what may be perceived to be a clumsy or inelegant (but usually relatively quick) solution to a problem.


A modification of a program to give the user access to features that were otherwise unavailable, unless the source code were open, would be called "cracking".

Get your terminology right. As described [here]("http://catb.org/esr/faqs/hacker-howto.html#what_is") by Eric Raymond. :)

---

### Post by Vostrocity on 2009-06-05
> Hack has several related meanings in the technology and computer science fields. It may refer to a clever or quick fix to a computer program problem, or to what may be perceived to be a clumsy or inelegant (but usually relatively quick) solution to a problem.

Whoever wrote that needs to rethink it. It can't be both a "clever.. fix" and a "clumsy.. solution". ;)

---

### Post by koenn on 2009-06-05
> **Vostrocity said:**
> Whoever wrote that needs to rethink it. It can't be both a "clever.. fix" and a "clumsy.. solution". ;)
Yes, it can.

---

