---
title: "C Source code found in Seamonkey Cache"
date: 2011-11-08
forum: Security
---

### Post by SparTacux on 2011-11-08
Ok - the last few visits to this site I noticed links going to Yahoo on 77.238.187.243. Javascript was turned on. I did some digging around in my Seamonkey Browser Cache folder and found a C source code program named 2548f59cd01 in there. I cleared my browsers Private Data to empty the cache and checked again and verified that the C source code was being delivered by this Forum. When Javascript is off the file doesn't appear in the Cache. When Javascript is on this forums downloads the C source code ( with no extension ) into my Cache. Nautilus see's it as C source code and not Javascript. I'm guessing some sort of YAHOO API or something. Maybe someone can shed some light?

---

### Post by OpSecShellshock on 2011-11-08
> **SparTacux said:**
> Ok - the last few visits to this site I noticed links going to Yahoo on 77.238.187.243. Javascript was turned on. I did some digging around in my Seamonkey Browser Cache folder and found a C source code program named 2548f59cd01 in there. I cleared my browsers Private Data to empty the cache and checked again and verified that the C source code was being delivered by this Forum. When Javascript is off the file doesn't appear in the Cache. When Javascript is on this forums downloads the C source code ( with no extension ) into my Cache. Nautilus see's it as C source code and not Javascript. I'm guessing some sort of YAHOO API or something. Maybe someone can shed some light?

Yes, there is Yahoo API code on this site, for example I'm pretty sure that's what gets used when posting with the editor. If you use NoScript with everything blocked by default, you'll notice that in order to use this site you need to enable both ubuntuforums.org and yahooapis.com.

---

### Post by SparTacux on 2011-11-08
False Alarm. It's not C code that's for sure. There's no main(  ) { code }  in the text. Probably PHP - although I've never used it. It uses return statements to end subroutines. I checked my logs and sure enough those Yahoo links go back quite a few weeks to my last install. I guess PHP can be used to hack your system tho - I had a look on the wiki page about PHP vulnerabilities. I've been too lazy to install NOSCRIPT on this install hence I didn't spot it.

---

### Post by lisati on 2011-11-08
I'd be surprised if it was PHP. PHP is like a script that gets used by the server to prepare HTML to send to your browser, the PHP code doesn't normally make it to your browser.

---

### Post by SparTacux on 2011-11-08
> **lisati said:**
> I'd be surprised if it was PHP. PHP is like a script that gets used by the server to prepare HTML to send to your browser, the PHP code doesn't normally make it to your browser.

 I'll post a sample and let you decide..

---

### Post by SparTacux on 2011-11-08
```
if(!window.console||!console.firebug){window.console={};var names=[&quot;log&quot;,&quot;debug&quot;,&quot;info&quot;,&quot;warn&quot;,&quot;error&quot;,&quot;assert&quot;,&quot;dir&quot;,&quot;dirxml&quot;,&quot;group&quot;,&quot;groupEnd&quot;,&quot;time&quot;,&quot;timeEnd&quot;,&quot;count&quot;,&quot;trace&quot;,&quot;profile&quot;,&quot;profileEnd&quot;];for(var i=0;i0);var is_saf=(YAHOO.env.ua.webkit>0);var is_webtv=(userAgent.indexOf(&quot;webtv&quot;)!=-1);var is_ie=((YAHOO.env.ua.ie>0)&&(!is_opera)&&(!is_saf)&&(!is_webtv));var is_ie4=(YAHOO.env.ua.ie==4);var is_ie7=(YAHOO.env.ua.ie>=7);var is_ps3=(userAgent.indexOf(&quot;playstation 3&quot;)!=-1);var is_moz=(YAHOO.env.ua.gecko>0);var is_kon=(userAgent.indexOf(&quot;konqueror&quot;)!=-1);var is_ns=((userAgent.indexOf(&quot;compatible&quot;)==-1)&&(userAgent.indexOf(&quot;mozilla&quot;)!=-1)&&(!is_opera)&&(!is_webtv)&&(!is_saf));var is_ns4=((is_ns)&&(parseInt(navigator.appVersion)==4));var is_mac=(userAgent.indexOf(&quot;mac&quot;)!=-1);var pointer_cursor=(is_ie?&quot;hand&quot;:&quot;pointer&quot
```

---

### Post by SparTacux on 2011-11-08
I haven't a clue what that is.

---

### Post by lisati on 2011-11-08
> **SparTacux said:**
> ```
if(!window.console||!console.firebug){window.console={};var names=[&quot;log&quot;,&quot;debug&quot;,&quot;info&quot;,&quot;warn&quot;,&quot;error&quot;,&quot;assert&quot;,&quot;dir&quot;,&quot;dirxml&quot;,&quot;group&quot;,&quot;groupEnd&quot;,&quot;time&quot;,&quot;timeEnd&quot;,&quot;count&quot;,&quot;trace&quot;,&quot;profile&quot;,&quot;profileEnd&quot;];for(var i=0;i0);var is_saf=(YAHOO.env.ua.webkit>0);var is_webtv=(userAgent.indexOf(&quot;webtv&quot;)!=-1);var is_ie=((YAHOO.env.ua.ie>0)&&(!is_opera)&&(!is_saf)&&(!is_webtv));var is_ie4=(YAHOO.env.ua.ie==4);var is_ie7=(YAHOO.env.ua.ie>=7);var is_ps3=(userAgent.indexOf(&quot;playstation 3&quot;)!=-1);var is_moz=(YAHOO.env.ua.gecko>0);var is_kon=(userAgent.indexOf(&quot;konqueror&quot;)!=-1);var is_ns=((userAgent.indexOf(&quot;compatible&quot;)==-1)&&(userAgent.indexOf(&quot;mozilla&quot;)!=-1)&&(!is_opera)&&(!is_webtv)&&(!is_saf));var is_ns4=((is_ns)&&(parseInt(navigator.appVersion)==4));var is_mac=(userAgent.indexOf(&quot;mac&quot;)!=-1);var pointer_cursor=(is_ie?&quot;hand&quot;:&quot;pointer&quot
```
I might be mistaken, but that looks more like Javascript to me.

---

### Post by SparTacux on 2011-11-08
I'll take your word for that. It didn't have a .js extension and Nautilus properties said file type being x-csrc  ????

---

### Post by Paddy Landau on 2011-11-09
That is Javascript. It's entirely normal for web pages. Don't worry about it.

---

### Post by SparTacux on 2011-11-09
Nah - I'm not too worried :-)

I had a late night on the Forum on Monday night & clicked on a couple of external links ( with javascript enabled ). Some of the guys had also been posting images located on external servers. My system clears the browser cache on exit. So I had a quick look in the Cache to see if anything interesting was there before going to bed . Nautilus said one of the file was C source code which set my alarm bells ringing.

One of the security tips I've come across is remove compilers so executables can't be assembled on your system. It was too late at night to look into it so I saved the contents of the Cache as a precaution. Further inspection proved it wasn't C source code. I'd spot that sort of thing a mile away - I was brought up on assembler and ANSI C in the 80's and 90's ;-)

I'm guessing from a security point of view that IF someone was going to hack your system with scripts then the likely location to find those scripts to be downloaded would be in the Browser Cache? The Cache on IE explorer on Microsoft Windows was easy enough to access. The Mozilla Directories in Ubuntu have weird and wonderful files that you can't access when you click on them. It looks like I've still got a bit of homework to do ;-) 

I'm not at all familar with Java, Javascript, PHP, Perl,etc. I ain't worked in computing since the mid 90's  The Code structure looks familiar enough though - some of it looks like it's modeled on C and I shouldn't have too much trouble getting to grips with this sort of stuff.

Ta for your contributions.

---

### Post by Paddy Landau on 2011-11-09
If you're happy, please mark the thread as solved.

---

