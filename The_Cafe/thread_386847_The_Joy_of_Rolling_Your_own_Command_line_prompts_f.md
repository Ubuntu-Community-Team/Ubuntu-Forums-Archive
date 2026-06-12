---
title: "The Joy of Rolling Your own Command line prompts for YubNub!"
date: 2007-03-17
forum: The Cafe
---

### Post by RAV TUX on 2007-03-17
YubNub and Linux are just meant too coexist....embrace Linux, embrace the Command Line...Embrace YubNub!

Share your favorite YubNub Command Line Prompts you have rolled....

here are some of mine:

ubfo = [http://ubuntuforums.org/](http://ubuntuforums.org/)

sx = [http://sabayonlinux.org/](http://sabayonlinux.org/)

c = [http://cafelinux.org/](http://cafelinux.org/)

linuxforum = [http://cafelinux.org/forum/](http://cafelinux.org/forum/)

one cutom made for me by the YubNub Dev,....

s.i <imagesearch>

also share your favorite existing Command Line Prompts

mine is 

gym <searchterm>

---

### Post by LookTJ on 2007-03-17
this commandline rocks!

you can create your commands

you also can search for commands by:

ls <query>

---

### Post by RAV TUX on 2007-03-17
> **Taylor said:**
> this commandline rocks!

you can create your commands

you also can search for commands by:

ls <query>

it is simple awesome try these:

c+++

radar

---

### Post by EdThaSlayer on 2007-03-17
What is this Yub Nub? I know it has something to do with commands but Wikipedia only gave me this definition. 
> Ewok Celebration (also known as Yub Nub from its incipit, which means 'freedom' in Ewokese) is a musical theme recurring in the ending of the Return of the Jedi. It was composed by John Williams.
I do hope its something good :) .

---

### Post by RAV TUX on 2007-03-17
> **EdThaSlayer said:**
> What is this Yub Nub? I know it has something to do with commands but Wikipedia only gave me this definition. 

I do hope its something good :) .YubNub is Command Lines for the web....and it defaults to a Google Search....


[http://yubnub.org/](http://yubnub.org/)

---

### Post by RAV TUX on 2007-03-17
> **EdThaSlayer said:**
> What is this Yub Nub? I know it has something to do with commands but Wikipedia only gave me this definition. 

I do hope its something good :) .
> **Saturday, June 04, 2005**

                                          **  	   	 YubNub: My entry for the Rails Day 24 hour programming contest  	       **

                                 [CENTER][[IMG]http://photos9.flickr.com/17515393_ef00ae333b_o.png[/IMG]]("http://yubnub.org/")
[/CENTER]
 [CENTER](Credit for the cute snail drawing goes to [Igor Križanovskij]("http://commons.wikimedia.org/wiki/Image:SCN1B.jpg"))
[/CENTER]

Well I have completed my submission for the 2005 "Rails Day" 24-hour programming contest. The idea was to make the coolest program in 24 hours, using a wonderful programming system called [Ruby on Rails]("http://www.google.com/url?sa=U&start=1&q=http%3A//www.rubyonrails.org/&ei=BYiiQsOdDpq2YLjH0KIE"). I made a web application called [YubNub]("http://yubnub.org/") (haven't had a chance to make it publicly accessible -- will do soon). But first, a question:

**1. What is YubNub?**

YubNub is a command-line for the web. After setting it up on your browser, you simply type "gim porsche 911" to do a [Google Image Search]("http://images.google.com/") for pictures of Porsche 911 sports cars. Type "random 49" to return random numbers between 1 and 49, courtesy of [random.org]("http://random.org/"). And best of all, you can make a new command by giving YubNub an appropriate URL.

**2. Why did you make YubNub?**

On a practical note, I was tired of setting up the same Firefox keywords on each of the 5 computers that I use. By putting my keywords into YubNub, I can hit "am mark twain" for an Amazon search, or "gmap vancouver" for a Google Maps search, no matter which computer I'm on.

But on a bigger scale, YubNub is the realization of a very big idea: the [URL command line]("http://udell.roninhouse.com/bytecols/2001-08-15.html") of the [web OS]("http://www.kottke.org/04/04/google-operating-system").

Web applications were once considered slow and unreliable, compared to their desktop counterparts. But these days, people are increasingly choosing web applications over desktop applications. Amazingly, GMail is found to be [faster]("http://jeremy.zawodny.com/blog/archives/004689.html") than desktop email programs. The snappy Google Maps interface feels as responsive as a desktop application. The web is morphing into the desktop, and today we are witness to the command line making its appearance in this new world, as YubNub, the (social) command-line for the web.

The beauty of YubNub is that anyone can help to extend it. If there is an existing web service with a submit form, they can add it pretty easily (like I did with the Amazon example above). But even more interesting is the adding of complex data-processing services (like validating an RSS feed, or converting webpages to audio using text-to-speech).

This will really come into play when I implement pipes (e.g. "google jon udell | to_rss | xargs text_to_speech"). Now *that *is going to rock! And I don't have to be the one to make these commands -- anyone in the world can create the code for [FONT=courier new]to_rss[/FONT], [FONT=courier new]xargs[/FONT], and [FONT=courier new]text_to_speech[/FONT], hosting it on their server. YubNub is just the glue that enables these pieces to interact.

**3. What's up with the name "YubNub", anyway?**

I remember hearing this word as a kid, watching one of the Star Wars movies. Evidently it means "[Hooray]("http://www.geocities.com/wermosguidetohuttese/Ewok.html")" in the Ewok language.            
            posted by Jonathan at        [6/04/2005 04:28:00 PM]("http://jonaquino.blogspot.com/2005/06/yubnub-my-entry-for-rails-day-24-hour.html") [http://jonaquino.blogspot.com/2005/06/yubnub-my-entry-for-rails-day-24-hour.html](http://jonaquino.blogspot.com/2005/06/yubnub-my-entry-for-rails-day-24-hour.html)

---

### Post by RAV TUX on 2007-03-17
> **EdThaSlayer said:**
> What is this Yub Nub? I know it has something to do with commands but Wikipedia only gave me this definition. 

I do hope its something good :) .

> **Advanced Syntax for Creating Commands**

   You probably already know that you can use %s to let the user specify parameters for your command. For example, if you make a command called gim with the following URL... [http://images.google.com/images?q=%s](http://images.google.com/images?q=%s)
 ...when the user types... gim porsche 911
 ...they will be taken to... [http://images.google.com/images?q=porsche+911](http://images.google.com/images?q=porsche+911)
 Below are some advanced tricks that you can use when making a new command. If you have any suggestions for advanced YubNub syntax, [EMAIL="jonathan.aquino@gmail.com"]send me an email[/EMAIL].  **Multiple Parameters**

 Finally YubNub now has multiple parameters. This is best explained with an example. Andrew MacDaniel wanted to make a [Google Local]("http://www.google.com/lochp") command called "gloc". Google Local takes two parameters: a "what" and a "where". You can now make such a command using the following URL:
[http://www.google.com/local?sc=1&hl=en&q=](http://www.google.com/local?sc=1&hl=en&q=)[COLOR=red]${what}[/COLOR]&near=[COLOR=red]${where}[/COLOR]&btnG=Google+Search&rl=1
 Note the two parameters: [COLOR=red]${what}[/COLOR] and [COLOR=red]${where}[/COLOR]. So now people can type... gloc -what [COLOR=red]pizza[/COLOR] -where [COLOR=red]Poughkeepsie, NY[/COLOR]
 ...and they will be taken to... [http://www.google.com/local?sc=1&hl=en&q=](http://www.google.com/local?sc=1&hl=en&q=)[COLOR=red]pizza[/COLOR]&near=[COLOR=red]Poughkeepsie%2C+NY[/COLOR]&btnG=Google+Search&rl=1
 Neat, hey? *Note the dashes on "-what" and "-where". This is a tribute to YubNub's command-line heritage. In the command-line world, these are called "switches". "-what" and "-where" would be referred to as the "what switch" and the "where switch".*  **Default Values**

 Continuing our above example, what if the user doesn't specify a "what" or a "where"? There is now a way to specify default values (syntax suggested by Christopher Church). [http://www.google.com/local?sc=1&hl=en&q=](http://www.google.com/local?sc=1&hl=en&q=)[COLOR=red]${what=tennis shoes}[/COLOR]&near=[COLOR=red]${where=Washington, DC}[/COLOR]&btnG=Google+Search&rl=1
 Now if the user does not specify a "what"... gloc -where Poughkeepsie, NY
 ...it will default to "tennis shoes" and they will be taken to... [http://www.google.com/local?sc=1&hl=en&q=](http://www.google.com/local?sc=1&hl=en&q=)[COLOR=red]tennis+shoes[/COLOR]&near=[COLOR=red]Poughkeepsie%2C+NY[/COLOR]&btnG=Google+Search&rl=1
 Similarly, if they do not specify a "where", it will default to "Washington, DC".  **Converting GET to POST**

 Sometimes you can't turn a web submission form into a YubNub command because it is a POST form (the source code says *method="post"*) rather than a GET form (the regular kind). Well, Sean O'Hagan has made a way to create YubNub commands from POST forms. All you have to do is include the following text somewhere in your URL: [post]

For example, here is the URL for the stlclib command, which searches the St. Louis County Library: [http://webpac.slcl.org/search/~a?a&searchtype=Y&searcharg=%s&searchscope=22](http://webpac.slcl.org/search/~a?a&searchtype=Y&searcharg=%s&searchscope=22)[post]
 Thanks Sean for contributing the get2post.php script! ([Source code]("http://jonaquino.textdriven.com/sean_ohagan/get2post.php.html"))

**Tip:** It can be a headache to try to construct the URL by looking at the HTML source. So go to [Stephen Ostermiller's bookmarklets]("http://ostermiller.org/bookmarklets/form.html") and drag his "Forms To GET" bookmarklet to your toolbar. Then press it to convert the POST form to a GET form so you can see the parameters in your address bar when you submit it.

**Update:** Joshua H. reports that when using [post] you may need to replace your "&" with a "?": *"I suspect that this wasn't noticed before because most search forms take more than one parameter and the important one with the search terms was not the first one in the list."* Some commands need it to be "&" (like [ibands]("http://yubnub.org/kernel/man?args=ibands")); others need it to be "?" (like [desa]("http://yubnub.org/kernel/man?args=desa")).  **Using a Character Other Than + for Spaces**

 Normally YubNub will convert spaces to + signs, like in the example above ("porsche 911" is converted to "porsche+911"). This is what most websites expect (like Google and Yahoo). But there are some websites that expect %20 instead of + signs -- for example, the National Library of Singapore. To tell YubNub to use %20 instead of + for spaces, include the following text somewhere in your URL: [use %20 for spaces].

For example, if you make a command called nlb with the following URL... [http://vistaweb.nlb.gov.sg/cgi-bin/cw_cgi?10100+REDIRX+useDatabase_3002_w_%s](http://vistaweb.nlb.gov.sg/cgi-bin/cw_cgi?10100+REDIRX+useDatabase_3002_w_%s)[use %20 for spaces]
 ...when the user types... nlb harry potter
 ...they will be taken to... [http://vistaweb.nlb.gov.sg/cgi-bin/cw_cgi?10100+REDIRX+useDatabase_3002_w_harry](http://vistaweb.nlb.gov.sg/cgi-bin/cw_cgi?10100+REDIRX+useDatabase_3002_w_harry)[COLOR=red]%20[/COLOR]potter
 Note that YubNub converted "harry potter" to "harry%20potter" instead of "harry+potter". 

**Update:** You can now use other characters besides %20. For example, to use - signs, say [use - for spaces].  **Turning off URL Encoding**

 Normally YubNub will apply "URL encoding" to parameters. For example, "gim Mork & Mindy" gets turned into [http://images.google.com/images?q=Mork](http://images.google.com/images?q=Mork)[COLOR=red]+%26+[/COLOR]Mindy (note that the & became +%26+). This is what works for most websites. However, W. Van Hooste pointed out that this does not work for the Internet Archive Wayback Machine. To tell YubNub to turn off URL encoding, include the following text somewhere in your URL: [no url encoding]

For example, if you make a command called arch with the following URL... [http://web.archive.org/web/*/%s](http://web.archive.org/web/*/%s)[no url encoding]
 ...when the user types... arch [http://www.ing.be/](http://www.ing.be/)
 ...they will be taken to... [http://web.archive.org/web/*/http://www.ing.be/](http://web.archive.org/web/*/http://www.ing.be/)
 If you hadn't specified [no url encoding], the user would have been taken to [http://web.archive.org/web/*/http%3A%2F%2Fwww.ing.be%2F](http://web.archive.org/web/*/http%3A%2F%2Fwww.ing.be%2F) **Combining Commands**

 You can now [combine commands together]("http://yubnub.blogspot.com/2005/07/ok-weve-got-pipes-how-to-combine.html"). For example, g {random 100}.  **Going to a Different URL Depending on Whether the User Supplies Parameters**

 Fuska has developed a [technique]("http://yubnub.blogspot.com/2005/08/first-command-to-use-ifthen-command.html") for going to one URL if the user provides arguments, and another URL if they do not provide arguments. For example, you can make a command that takes you to the CNN search page if you specify keywords to search for, and if you don't specify any keywords, it will take you to the CNN main page. Fuska's technique uses [Allen Ormond's ifthen command]("http://yubnub.blogspot.com/2005/08/allen-ormonds-programmatic-commands.html").  **Positional Parameters**

 Fuska has also developed a technique for [positional parameters]("http://yubnub.blogspot.com/2005/12/positional-parameters-problem-solved.html") e.g. gloc -what [COLOR=red]{% 1 %s}[/COLOR] -where [COLOR=red]{% 2 %s}[/COLOR][no url encoding][http://yubnub.org/documentation/describe_advanced_syntax](http://yubnub.org/documentation/describe_advanced_syntax)

---

### Post by RAV TUX on 2007-03-17
> [B][[IMG]http://photos9.flickr.com/17515393_ef00ae333b_o.png[/IMG]]("http://yubnub.blogspot.com/")
     [  	]("http://yubnub.blogspot.com/")   [/B]

   News about YubNub.org
   
                  **Friday, December 16, 2005**

                                  ** 	  	 Positional parameters problem solved by fuska 	      **

       	          	       fuska is very clever.

He implemented positional parameters by creating a command called %. Yes it is called %. So essentially you can do % 1, % 2, % 3, etc.

For example, the googlocal command:

gloc -what {% 1 %s} -where {% 2 %s}[no url encoding]

I was quite stunned when I saw this example, and it took me a couple of minutes to understand how % works its magic. I am so impressed.
     
     
                 *posted by Jonathan at **[12/16/2005 11:35:00 PM]("http://yubnub.blogspot.com/2005/12/positional-parameters-problem-solved.html")*[http://yubnub.blogspot.com/2005/12/positional-parameters-problem-solved.html](http://yubnub.blogspot.com/2005/12/positional-parameters-problem-solved.html)*[]("http://yubnub.blogspot.com/2005/12/positional-parameters-problem-solved.html")*

---

### Post by RAV TUX on 2007-03-17
> **Golden Eggs (ge)**

           [IMG]http://yubnub.org/images/ge.jpg[/IMG]     Thanks to [Jacob Ensor]("http://jjefferydesign.com/") 
for the beautiful egg logo
   
   [[IMG]http://yubnub.org/images/xml_button.gif[/IMG]]("http://yubnub.org/golden_eggs.xml")       Welcome to YubNub Golden Eggs! The Golden Eggs are YubNub commands that people seem to find particularly   useful and interesting. If you want to nominate a YubNub command for this list,   [EMAIL="jonathan.aquino@gmail.com?subject=Nomination%20for%20a%20YubNub%20Golden%20Egg&body=Hey%20Jon,%20there%27s%20a%20great%20command%20that%20I%20want%20to%20see%20on%20the%20Golden%20Egg%20list:%20%5Binsert%20command%20here%5D"]email Jon[/EMAIL]   about it.       
       [COLOR=red]Tip:[/COLOR] You can search the Golden Eggs -- for example: ge dictionary   
   
   **esvgrk**      
View the English Standard Version of the Bible (ESV) in parallel with the Greek New Testament or Septuagint (Old Testament). Example: esvgrk John 3:16-18
     22 uses   -   Created 2007-03-02 16:14   -   Last used 2007-03-17 21:04   -         [Description]("http://yubnub.org/kernel/man?args=esvgrk")   -   splitv {url grkbib %s} {url esv %s}
  
   **esv**      
Look up the text of a Bible passage in the English Standard Version. examples: esv joshua 1:9 esv ecclesiastes 3 esv 1 cor. 13 esv john 19:17-22
     83 uses   -   Created 2007-02-21 04:47   -   Last used 2007-03-17 21:04   -         [Description]("http://yubnub.org/kernel/man?args=esv")   -   [http://www.gnpcb.org/esv/search/?q=%s](http://www.gnpcb.org/esv/search/?q=%s)
  
   **hoogle**      
The Haskell API Search Engine. Hoogle allows you to search by either name, or by approximate type signature. Example searches: hoogle map hoogle (a -> b) -> [a] -> [b] hoogle Ord a => [a] -> [a]
     330 uses   -   Created 2005-10-31 16:48   -   Last used 2007-03-17 00:47   -         [Description]("http://yubnub.org/kernel/man?args=hoogle")   -   [http://haskell.org/hoogle/?q=%s](http://haskell.org/hoogle/?q=%s)
  
   **+s**      
Uses the opensearch command to add YubNub commands to the search bar in your browser. Added engines are somewhat ugly since we cannot add any real metadata to YubNub commands yet. AUTHOR Stephen Paul Weber [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/)
     57 uses   -   Created 2007-01-23 01:09   -   Last used 2007-03-17 16:50   -         [Description]("http://yubnub.org/kernel/man?args=%2Bs")   -   echo <script type="text/javascript">window.external.AddSearchProvider("{url opensearch %s}");</script> <i>Adding search engine...</i>
  
   **opensearch**      
NAME opensearch - Creates OpenSearch XML for a YubNub command SYNOPSIS opensearch [YUBNUB COMMAND] EXAMPLES opensearch g opensearch ls NOTES This kind of functionality, if YubNub supported it, could be even cooler. If YubNub let us actually specify different kinds of URLs for commands (and the other kinds of parameters OpenSearch has natively) YubNub would be like an OpenSearch over-layer for the web. AUTHOR Stephen Paul Weber [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/)
     114 uses   -   Created 2007-01-23 01:03   -   Last used 2007-03-17 16:50   -         [Description]("http://yubnub.org/kernel/man?args=opensearch")   -   [http://singpolymaplay.ning.com/yubnub-opensearch.php?xn_auth=no&cmd=%s](http://singpolymaplay.ning.com/yubnub-opensearch.php?xn_auth=no&cmd=%s)
  
   **fooplot**      
        Graphing calculator and plotter (SVG and VML based). Example: fooplot tan(x)
     367 uses   -   Created 2007-01-05 06:05   -   Last used 2007-03-16 08:43   -         [Description]("http://yubnub.org/kernel/man?args=fooplot")   -   [http://fooplot.com/index.php?q0=%s](http://fooplot.com/index.php?q0=%s)[no url encoding]
  
   **qdef**      
This command loads definitions from the excellent ninjawords.com. It automatically closes the definition window in 10 seconds. To change the length that the window is open, use the -t parameter. NOTES Your browser must be set to allow pop-ups from yubnub.org" The technique this command uses is a short javascript program with a setTimeout event. A YubNub echo command just loads the javascript onto a webpage. Here is the javascript: <script> def=window.open('http://www.ninjawords.com/%s'); /* ope...
     392 uses   -   Created 2006-12-13 22:55   -   Last used 2007-03-17 14:29   -         [Description]("http://yubnub.org/kernel/man?args=qdef")   -   echo <script>def=window.open('http://www.ninjawords.com/%s');setTimeout("def.close();history.go(-1);",${t=10}000);</script>
  
   **faf**      
        Fire and forget. Runs the yubnub command and then goes back to the page you were on.
     291 uses   -   Created 2006-12-11 18:43   -   Last used 2007-03-13 13:22   -         [Description]("http://yubnub.org/kernel/man?args=faf")   -   echo <iframe src="{url %s}" onload="history.go(-1)" style="display:none">
  
   **twu**      
        Updates your twitter status and then redirects to the twitter homepage.
     69 uses   -   Created 2006-12-11 16:53   -   Last used 2007-03-15 17:06   -         [Description]("http://yubnub.org/kernel/man?args=twu")   -   both twiu %s -and twi
  
   **both**      
        Executes 2 yubnub commands in sequence (client-side) Example: both command1 -and command2
     135 uses   -   Created 2006-12-11 16:49   -   Last used 2007-03-15 23:08   -         [Description]("http://yubnub.org/kernel/man?args=both")   -   echo <iframe src="{url %s}" onload="location='{url ${and}}'" style="display:none">
  
   **din**      
DomainInspector Dynamic Yubnub webpage utility created to inspect domains names/ip addresses Can also be used for key word searches against virus KBs Google and Yahoo ~jbrown~ Usage: din
     151 uses   -   Created 2006-12-10 23:52   -   Last used 2007-03-16 21:15   -         [Description]("http://yubnub.org/kernel/man?args=din")   -   [http://yubnub.org/example/echo?text=%3Cscript+type%3D%22text%2Fjavascript%22%3Efunction+dw%28%29%7B%0D%0Ae%3Ddocument%2Eforms%5B0%5D%2Ee%0D%0Atxt%3D%22%22%0D%0Aerl%3D%22http%3A%2F%2Fyubnub%2Eorg%2Fparser%2Fparse%3Fcommand%3Dmash+%22%0D%0Ax%3Ddocument%2Eforms%5B0%5D%2EF%2Evalue%0D%0Afor+%28i%3D0%3Bi%3Ce%2Elength%3B%2B%2B+i%29%7Bif+%28e%5Bi%5D%2Echecked%29%7Btxt%3Dtxt+%2B+e%5Bi%5D%2Evalue+%2B+%22%22+%7D%7Dwindow%2Eopen%28erl%2B+x+%2B+txt%29%3B%7D%0D%0A%3C%2Fscript%3EDomainInspect%3Cbr%3E%3C%2Fa%3E%3Cform%3E%3Cinput+name%3D%22F%22+size%3D%2250%22+value%3D%22%22+type%3D%22text%22%3E%3Cinput+onclick%3D%22dw%28%29%22+value%3D%22Submit%22+type%3D%22button%22%3E+%3CINPUT+TYPE%3DRESET+VALUE%3D%22Reset%22%3E%3Cbr%3E%3Cinput+name%3D%22e%22+value%3D%22+ping%22+type%3D%22checkbox%22%3EPing%3Cinput+name%3D%22e%22+value%3D%22+tracert%22+type%3D%22checkbox%22%3ETraceroute%3Cinput+name%3D%22e%22+value%3D%22+safe%22+type%3D%22checkbox%22%3ESiteAdvisor%3Cinput+name%3D%22e%22+value%3D%22+dnsloc%22+type%3D%22checkbox%22%3EIPLocation%3Cbr%3E%3Cinput+name%3D%22e%22+value%3D%22+whof%22+type%3D%22checkbox%22%3EDNSStuff%3Cinput+name%3D%22e%22+value%3D%22+Netcraft%22+type%3D%22checkbox%22%3ENetcraft%3Cinput+name%3D%22e%22+value%3D%22+dd%22+type%3D%22checkbox%22%3EDomDossier%3Cinput+name%3D%22e%22+value%3D%22+dnsrbl%22+type%3D%22checkbox%22%3ERobtex%3Cinput+name%3D%22e%22+value%3D%22+g%22+type%3D%22checkbox%22%3EGoogle%3Cinput+name%3D%22e%22+value%3D%22+ysite%22+type%3D%22checkbox%22%3EYahoo%3Cbr%3E%3Cinput+name%3D%22e%22+value%3D%22+virus%22+type%3D%22checkbox%22%3ESymantec+%3Cinput+name%3D%22e%22+value%3D%22+vir%22+type%3D%22checkbox%22%3ETrend%3Cinput+name%3D%22e%22+value%3D%22+kavs%22+type%3D%22checkbox%22%3EKaprsky%3Cinput+name%3D%22e%22+value%3D%22+sofo%22+type%3D%22checkbox%22%3ESophos%3Cinput+name%3D%22e%22+value%3D%22+wbm%22+type%3D%22checkbox%22%3EWayback%3C%2Fform%3E%3Ca+href%3D%22http%3A%2F%2Fwww%2Evirustotal%2Ecom%22+%3EVirusTotal%3C%2Fa%3E%3Cbr%3E%3Ca+href%3D%22http%3A%2F%2Fwww%2EAlexa%2Ecom%22%3EAlexa%3C%2Fa%3E](http://yubnub.org/example/echo?text=%3Cscript+type%3D%22text%2Fjavascript%22%3Efunction+dw%28%29%7B%0D%0Ae%3Ddocument%2Eforms%5B0%5D%2Ee%0D%0Atxt%3D%22%22%0D%0Aerl%3D%22http%3A%2F%2Fyubnub%2Eorg%2Fparser%2Fparse%3Fcommand%3Dmash+%22%0D%0Ax%3Ddocument%2Eforms%5B0%5D%2EF%2Evalue%0D%0Afor+%28i%3D0%3Bi%3Ce%2Elength%3B%2B%2B+i%29%7Bif+%28e%5Bi%5D%2Echecked%29%7Btxt%3Dtxt+%2B+e%5Bi%5D%2Evalue+%2B+%22%22+%7D%7Dwindow%2Eopen%28erl%2B+x+%2B+txt%29%3B%7D%0D%0A%3C%2Fscript%3EDomainInspect%3Cbr%3E%3C%2Fa%3E%3Cform%3E%3Cinput+name%3D%22F%22+size%3D%2250%22+value%3D%22%22+type%3D%22text%22%3E%3Cinput+onclick%3D%22dw%28%29%22+value%3D%22Submit%22+type%3D%22button%22%3E+%3CINPUT+TYPE%3DRESET+VALUE%3D%22Reset%22%3E%3Cbr%3E%3Cinput+name%3D%22e%22+value%3D%22+ping%22+type%3D%22checkbox%22%3EPing%3Cinput+name%3D%22e%22+value%3D%22+tracert%22+type%3D%22checkbox%22%3ETraceroute%3Cinput+name%3D%22e%22+value%3D%22+safe%22+type%3D%22checkbox%22%3ESiteAdvisor%3Cinput+name%3D%22e%22+value%3D%22+dnsloc%22+type%3D%22checkbox%22%3EIPLocation%3Cbr%3E%3Cinput+name%3D%22e%22+value%3D%22+whof%22+type%3D%22checkbox%22%3EDNSStuff%3Cinput+name%3D%22e%22+value%3D%22+Netcraft%22+type%3D%22checkbox%22%3ENetcraft%3Cinput+name%3D%22e%22+value%3D%22+dd%22+type%3D%22checkbox%22%3EDomDossier%3Cinput+name%3D%22e%22+value%3D%22+dnsrbl%22+type%3D%22checkbox%22%3ERobtex%3Cinput+name%3D%22e%22+value%3D%22+g%22+type%3D%22checkbox%22%3EGoogle%3Cinput+name%3D%22e%22+value%3D%22+ysite%22+type%3D%22checkbox%22%3EYahoo%3Cbr%3E%3Cinput+name%3D%22e%22+value%3D%22+virus%22+type%3D%22checkbox%22%3ESymantec+%3Cinput+name%3D%22e%22+value%3D%22+vir%22+type%3D%22checkbox%22%3ETrend%3Cinput+name%3D%22e%22+value%3D%22+kavs%22+type%3D%22checkbox%22%3EKaprsky%3Cinput+name%3D%22e%22+value%3D%22+sofo%22+type%3D%22checkbox%22%3ESophos%3Cinput+name%3D%22e%22+value%3D%22+wbm%22+type%3D%22checkbox%22%3EWayback%3C%2Fform%3E%3Ca+href%3D%22http%3A%2F%2Fwww%2Evirustotal%2Ecom%22+%3EVirusTotal%3C%2Fa%3E%3Cbr%3E%3Ca+href%3D%22http%3A%2F%2Fwww%2EAlexa%2Ecom%22%3EAlexa%3C%2Fa%3E) 
  
   **topoz**      
topoz provides commandline access to the USGS topographic maps (hosted at Topozone.com) by referencing the latitude and longitude corresponding to the center of a Zip Code area (courtesy of GeoCoder.us). EXAMPLES Example: topoz 10004 Result: Displays online map of Ellis Island, New York. Example: topoz 95389 Result: Displays online map of Yosemite, California. SEE ALSO [http://geocoder.us/help/city_state_zip.shtml](http://geocoder.us/help/city_state_zip.shtml) AUTHOR Paul M. Boren pmboren AT gmail DOT com
     232 uses   -   Created 2006-10-25 04:34   -   Last used 2007-03-17 06:28   -         [Description]("http://yubnub.org/kernel/man?args=topoz")   -   http://www.topozone.com/map.asp?lat={idx {explode {http://geocoder.us/service/csv/geocode?zip=%s}} -idx 0}&lon={idx {explode {http://geocoder.us/service/csv/geocode?zip=%s}} -idx 1}
  
   **urlet**      
NAME urlet - Create a simple bookmarklet from a YubNub command that work on the current page. SYNOPSIS urlet [YUBNUB COMMAND] EXAMPLES urlet autotr Drag the resulting link to your bookmark bar. Click the bookmarklet to translate the current page to english. urlet whois Drag the resulting link to your bookmark bar. Click the bookmarklet to get WHOIS information on the current domain. AUTHOR [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/) Stephen Paul Weber
     91 uses   -   Created 2006-10-19 12:58   -   Last used 2007-03-02 19:43   -         [Description]("http://yubnub.org/kernel/man?args=urlet")   -   echo <a href="javascript:window.location='http://yubnub.org/parser/parse?command='+encodeURIComponent('%s '+window.location.href);">%s</a>[no url encoding]
  
   **delpost**      
Comando para salvar tus favoritos en del.icio.as creado por artux (cutepaste.wordpress.com) Modo de uso: delpost -u [url sin http://] -d [descripcion] e.g.: delpost -u artux.com.ar -d Blog personal de artux NOTA: solo para usuarios registrados de del.icio.us 
     32 uses   -   Created 2006-10-13 20:24   -   Last used 2007-02-25 23:33   -         [Description]("http://yubnub.org/kernel/man?args=delpost")   -   http://del.icio.us/post?v=4;url=${u};title=${d}
  
   **gdox**      
        Shortcut to [http://docs.google.com](http://docs.google.com) which combines Google spreadsheets and Writely files.
     423 uses   -   Created 2006-10-11 15:51   -   Last used 2007-03-17 18:31   -         [Description]("http://yubnub.org/kernel/man?args=gdox")   -   [http://docs.google.com](http://docs.google.com)
  
   **dluc**      
Optional arguments: -USER Your username or the username you want to specifically search. You can also use the keyword "TAG" to do a general search but filtered by a tag. Another possibility is using the keyword "POPULAR" to search the top ranked sites. Or the keyword "RECENT" which returns the last added url. That means diferents sites on every request. -TAG The tag you want to filter the results by. This argument is mandatory if the first one was "TAG". Has no effects if the first one was "REC...
     147 uses   -   Created 2006-10-08 18:25   -   Last used 2007-03-05 11:18   -         [Description]("http://yubnub.org/kernel/man?args=dluc")   -   yubnub {eatFeed items[-0].link -url http://del.icio.us/rss/{% 1 %s}/{% 2- %s}}
  
   **kzip**      
create a zip archive containing the files found at the given urls. the archive can then be downloaded or mailed. archive name and at least one file url are mandatory. AUTHOR Yann Perrin (see [http://yann.perrin.googlepages.com](http://yann.perrin.googlepages.com) for contact info)
     124 uses   -   Created 2006-09-28 17:59   -   Last used 2007-03-15 11:57   -         [Description]("http://yubnub.org/kernel/man?args=kzip")   -   http://krun.ch/home/wkrunch&file%5B%5D={% 2 %s[no url encoding]}&file%5B%5D={% 3 %s[no url encoding]}&file%5B%5D={% 4 %s[no url encoding]}&file%5B%5D={% 5 %s[no url encoding]}&file%5B%5D={% 6 %s[no url encoding]}&file%5B%5D={% 7 %s[no url encoding]}&file%5B%5D={% 8 %s[no url encoding]}&file%5B%5D={% 9 %s[no url encoding]}&file%5B%5D={% 10 %s[no url encoding]}&file%5B%5D={% 11 %s[no url encoding]}&file_name={% 1 %s[no url encoding]}&file_type=zip&x=&y=[post]
  
   **kidsof**      
Example: kidsof gim This will show you commands that use "gim" in their definition. Unfortunately, if there are more than a page of kids, they are omitted. Trying to iron out this problem.
     134 uses   -   Created 2006-09-14 03:19   -   Last used 2007-03-02 19:43   -         [Description]("http://yubnub.org/kernel/man?args=kidsof")   -   foreach {match -url {url ls %s} -pattern /args=(.*)" class.*\n.*\n.*hint">.*\n*?%s .*\n*?</ -capture 1} -cmd 2html
  
   **ReFilter**      
NAME ReFilter - Filter the contents of a RSS feed to recieve only specific topics. SYNOPSIS ReFilter -feed [Feed URL] -filter [keywords] ReFilter advanced sintaxis is here: [http://re.rephrase.net/filter/?p=filters](http://re.rephrase.net/filter/?p=filters) EXAMPLES ReFilter -feed [http://www.autohotkey.com/forum/rss.php](http://www.autohotkey.com/forum/rss.php) -filter title:function ReFilter -feed [http://www.thinkgeek.com/thinkgeek.rss](http://www.thinkgeek.com/thinkgeek.rss) -filter toy ReFilter (shows the basic GUI of the application) 
     45 uses   -   Created 2006-09-03 18:54   -   Last used 2007-03-12 15:08   -         [Description]("http://yubnub.org/kernel/man?args=ReFilter")   -   http://re.rephrase.net/filter/?{ifnotempty ${feed} -then feed=${feed}}{ifnotempty ${filter} -then &filter=${filter}}
  
   **wp\**      
NAME wp\ - Spell checks a word or phrase and then searches for it on the english wikipedia. SYNOPSIS wp\ [TERM] EXAMPLES wp\ age of empirs (Fetches the article on "Age of Empires") AUTHOR Allen Ormond - aormond (at) gmail (dot) coom
     142 uses   -   Created 2006-08-31 02:43   -   Last used 2007-03-15 17:51   -         [Description]("http://yubnub.org/kernel/man?args=wp%5C")   -   spll wp %s
  
   **clipget**      
NAME clipget - retrieve the text previously stored under the provided name, using cl1p.net SYNOPSIS clipget [name] EXAMPLES clipget obiwan will retrieve the text stored under the name "obiwan" at cl1p.net. the name argument is mandatory. NOTES related command : clipset AUTHOR Yann Perrin (see [http://yann.perrin.googlepages.com](http://yann.perrin.googlepages.com) for contact info)
     218 uses   -   Created 2006-09-07 13:01   -   Last used 2007-03-06 13:00   -         [Description]("http://yubnub.org/kernel/man?args=clipget")   -   [http://d.cl1p.net/%s/](http://d.cl1p.net/%s/)
  
   **clipset**      
NAME clipset - store the given text online under the provided name, using cl1p.net SYNOPSIS clipset [name] [optional text] EXAMPLES clipset obiwan was a great jedi will store the text "was a great jedi" under the name "obiwan" at cl1p.net for one week. this duration, and the text content can then be edited by going to [http://cl1p.net/obiwan/](http://cl1p.net/obiwan/) it is recommanded to password protect your text if don't want it to be editable by others. the name argument is mandatory. If it's allready in use and passw...
     52 uses   -   Created 2006-09-07 12:54   -   Last used 2007-03-04 00:43   -         [Description]("http://yubnub.org/kernel/man?args=clipset")   -   http://cl1p.net/{% 1 %s [no url encoding]}?ctrlcv={% 2- %s [no url encoding]}&title={% 1 %s [no url encoding]}&keepfor=10080&uploadFile=&p1=&p2=&addLink=&removeLink=&jump={% 1 %s [no url encoding]}[post]
  
   **l>>pdf**      
l>>pdf will do a Google search on the first hyphen-separated parameter, select the first result, then search for the second parameter within that site and return only the PDFs found there. It is useful if you want to search within a specific site for PDFs, but you don't know the URL or Yubnub command for that site. RELATED COMMANDS l>>, >>, lucky>, l>, lucky>>, mysearch AUTHOR This is a simple alias of Fuska's mysearch command (inspired by Shantanuo, see: [http://groups.google.com/group/YubNub/b](http://groups.google.com/group/YubNub/b)...
     51 uses   -   Created 2006-09-06 09:26   -   Last used 2007-02-21 19:25   -         [Description]("http://yubnub.org/kernel/man?args=l%3E%3Epdf")   -   lucky>> {% 1 %s} -k {% 2- %s} filetype:pdf
  
   **gsplit**      
gsplit allows you to search any combination of the below google search engines and have them split across your screen using split. Using more than 3 on a small resolution (<= 1024x768) isn't really recommended. Simply type gsplit and the query followed by the search engines you want to visit (e.g. -g or -i or -n) and a y after each one to indicate that [y]es [y]ou want [y]ubnub to search it. -a y - answers -A y - All included engines -b y - blogsearch -B y - books -c y - catalogs -f y - finance...
     1105 uses   -   Created 2006-08-12 22:51   -   Last used 2007-03-04 19:30   -         [Description]("http://yubnub.org/kernel/man?args=gsplit")   -   split {ifthen -value1 ${g} -value2 y -test EQUAL -then {url g %s}} {ifthen -value1 ${n} -value2 y -test EQUAL -then {url superg %s -t news}} {ifthen -value1 ${i} -value2 y -test EQUAL -then {url gi %s}} {ifthen -value1 ${B} -value2 y -test EQUAL -then {url superg %s -t books}} {ifthen -value1 ${c} -value2 y -test EQUAL -then {url superg %s -t catalogs}} {ifthen -value1 ${G} -value2 y -test EQUAL -then {url superg %s -t groups}} {ifthen -value1 ${m} -value2 y -test EQUAL -then {url superg %s -t maps}} {ifthen -value1 ${s} -value2 y -test EQUAL -then {url superg %s -t scholar}} {ifthen -value1 ${b} -value2 y -test EQUAL -then {url superg %s -t blogsearch}} {ifthen -value1 ${a} -value2 y -test EQUAL -then {url http://answers.google.com/answers/search?q=%s}} {ifthen -value1 ${f} -value2 y -test EQUAL -then {url http://finance.google.com/finance?q=%s}} {ifthen -value1 ${A} -value2 y -test EQUAL -then {url g %s} {url gi %s} {url gn %s} {url gbs %s} {url gcatalogs %s} {url gm %s} {url groups %s} {url gs %s} {url gfi %s} {url gans %s} {url goobooks %s} }
  
   **geo**      
Yuan.CC Maps is a service that allows you to view the location of Flickr photos and GPS tracks. It will also allow you to geotag your Flickr photos and upload your own GPS tracks. The "yuan" command searches the maps for an address. It defaults to load Flickr photos, but you can add "-service gps" to load GPS tracks. Optionally, the zoom level can be set using "-z". Zoom options are from 1 (the whole world) to 19 (street level). NOTES Thanks to CK Yuan for a great geotagging tool! This command ...
     112 uses   -   Created 2005-06-08 19:08   -   Last used 2007-03-11 13:43   -         [Description]("http://yubnub.org/kernel/man?args=geo")   -   http://maps.yuan.cc/?{eop address=@%s@&zoom=${z=13} -else zoom=${z=2}}&service=${service=flickr}
  
   **ylist2**      
NAME ylist2 - A slightly altered version of ylist SYNOPSIS ylist2 [YLIST NAME] EXAMPLES ylist2 yfr NOTES ylist2 was created for large ylists that far exceed the limitations of GET, and thus the echo command. All lists in ylist can be viewed-edited in ylist2 and vice-versa. Please see ylist for more details. AUTHOR Stephen Paul Weber [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/)
     70 uses   -   Created 2006-08-09 16:36   -   Last used 2007-03-05 21:11   -         [Description]("http://yubnub.org/kernel/man?args=ylist2")   -   echovar <h1>ylist %s</h1><ul>@var@</ul><form method="get" action="http://singpolymaplay.ning.com/form2yubnub.php?xn_auth=no"><div><input type="hidden" name="cmdstr" value="ylist2 %s%7Bdummy %7Bvar CE55FE36-D5D1-11DA-B35B-DD81D6839540:%s -set %7Bvar CE55FE36-D5D1-11DA-B35B-DD81D6839540:%s%7D<li>%25s</li>%7D%7D" />Add Item: <input type="text" name="%25s" /><input type="submit" value="Go" /></div></form> <form method="get" action="http://singpolymaplay.ning.com/form2yubnub.php?xn_auth=no"><div><input type="hidden" name="cmdstr" value="ylist2 %s%7Bdummy %7Bvar CE55FE36-D5D1-11DA-B35B-DD81D6839540:%s -set %7Bmatch %7Bridx &lt;ul&gt;%7Bvar CE55FE36-D5D1-11DA-B35B-DD81D6839540:%s%7D&lt;/ul&gt; -idx %25s -as xoxo%7D -pattern /&lt;ul class=&quot;xoxo&quot;&gt;(.*?)&lt;\/ul&gt;/ -capture 1 -matchnbr 1%7D%7D%7D" />Remove Item At: <input type="text" name="%25s" /><input type="submit" value="Go" /></div></form> -var CE55FE36-D5D1-11DA-B35B-DD81D6839540:%s[no url encoding]
  
   **echovar**      
The echo command is limited to the length of data it can output because it depends on GET. This command can insert the contents of large variables into your custom strings without this limitation. You can pass any legal MIME-type to -mime and the output will be done in that type. @var@ in the string is what will be replaced with the value of the variable. AUTHOR Stephen Paul Weber [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/)
     90 uses   -   Created 2006-08-09 16:28   -   Last used 2007-03-05 21:11   -         [Description]("http://yubnub.org/kernel/man?args=echovar")   -   http://singpolymaplay.ning.com/yubnub-echovar.php?xn_auth=no&txt=%s&var=${var}&content-type=${mime}
  
   **rands**      
NAME rands - Search on a random search engine. SYNOPSIS rands [KEYWORDS] EXAMPLES rands yubnub Searches for 'yubnub' on a random one of Google, Yahoo, or another search engine supported. NOTES Search engine data is stored as an array in the variable rands-data. To view the list type: var rands-data To add an item to the list type: ava rands-data -a COMMAND NAME AUTHOR Stephen Paul Weber [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/)
     78 uses   -   Created 2006-08-10 23:20   -   Last used 2007-03-16 11:37   -         [Description]("http://yubnub.org/kernel/man?args=rands")   -   yubnub {idx {var rands-data} -idx {random -min 0 -max {clc {count {var rands-data}}-1}}} %s
  
   **-**      
NAME - - YubNub 'domains' SYNOPSIS - ['DOMAIN'] -set [URL] -/ [DIRECTORY] EXAMPLES - singpolyma -set http://singpolyma-tech.blogspot.com/ Set the 'domain' singpolyma to http://singpolyma-tech.blogspot.com/ and then go there to test - singpolyma Go to the URL which the 'domain' singpolyma is set to - singpolyma -/ 2006/01/comment-aggregation.html Go to a specific file under the URL which singpolyma references AUTHOR Stephen Paul Weber http://singpolyma-tech.blogspot.com/
     508 uses   -   Created 2006-08-08 13:35   -   Last used 2007-03-17 20:04   -         [Description]("http://yubnub.org/kernel/man?args=-")   -   {var 0fe27a11-f265-4c3b-8cb9-bd7b7691959d:%s -set ${set=do not set : tes ton od}}${/}[no url encoding]
  
   **superg**      
superg is one big command that supports all of the Google Search types except for video and directory (those two were left out because their implementation would have greatly increased the complexity of the command and I'm not sure many people use them) If no -t is passed a standard Google websearch is performed. The following are the valid values for -t: blogsearch books catalogs groups images maps news scholar lucky AUTHOR Stephen Paul Weber [http://singpolyma-tech.blogspot.com/](http://singpolyma-tech.blogspot.com/)
     8082 uses   -   Created 2006-08-08 00:18   -   Last used 2007-03-06 05:04   -         [Description]("http://yubnub.org/kernel/man?args=superg")   -   http://{ifthen -value1 ${t} -value2 lucky -test EQUAL -then www -else ${t=www}}.google.com/{ifthen -value1 ${t} -value2 lucky -test EQUAL -then search -else ${t=search}}?q=%s{ifthen -value1 ${t} -value2 lucky -test EQUAL -then &btnI=I%27m+Feeling+Lucky -else}
  
   **delete**      
        To delete a tag from all your flickr photos which contain that specific tag for e.g. delete testing
     48 uses   -   Created 2006-08-02 12:02   -   Last used 2007-03-17 19:06   -         [Description]("http://yubnub.org/kernel/man?args=delete")   -   [http://flickr.com/photos/me/tags/%s/delete](http://flickr.com/photos/me/tags/%s/delete)
  
   **luckygim**      
Performs a Google Image Search using the given keywords and displays the first 20 images, full-size. Not for the faint of bandwidth. AUTHOR Eliazar elzr.com SEE ALSO The lucky family of commands: luckyxim, >, >>, >>>, l>, l>>, <, <<, <<<, luckyecho
     336 uses   -   Created 2006-08-03 05:06   -   Last used 2007-03-15 17:52   -         [Description]("http://yubnub.org/kernel/man?args=luckygim")   -   [http://elzr.com/yubnub/luckygim/%s](http://elzr.com/yubnub/luckygim/%s)
  
   **ffim**      
        FindForward Image Search Usage: ffim [keyword] b.a.
     1323 uses   -   Created 2005-07-10 03:44   -   Last used 2007-03-15 14:23   -         [Description]("http://yubnub.org/kernel/man?args=ffim")   -   [http://findforward.com/direct/?q=%s](http://findforward.com/direct/?q=%s)
  
   **l>>**      
This command is allows you to do a search within a given site. The first parameter should describe the site you are looking for. It will do a Google search on the first parameter, select the first result, then search for the second parameter within that site. This is a shorter version of the lucky>> command. NOTES Related commands: lucky>, l>, lucky>> This command uses Allen Ormond's "param" command. Inspired by Eliazar Parra's > and luckyecho commands, that latter of which uses Sean O'Hagan's ...
     256 uses   -   Created 2006-07-31 22:24   -   Last used 2007-03-14 08:31   -         [Description]("http://yubnub.org/kernel/man?args=l%3E%3E")   -   lucky>> {param s;k %s}
  
   **lucky>>**      
This command is allows you to do a search within a given site. The first parameter should describe the site you are looking for. The -k parameter is the search term you are trying to find within the site. It is useful if you want to search within a specific site, but you don't know the URL or Yubnub command for that site. NOTES Related commands: lucky>, l> Inspired by Eliazar Parra's >> and luckyecho commands, that latter of which uses Sean O'Hagan's scrape command. AUTHOR Brian Armknecht b.a.
     438 uses   -   Created 2006-07-31 22:11   -   Last used 2007-03-14 08:31   -         [Description]("http://yubnub.org/kernel/man?args=lucky%3E%3E")   -   g site:{ extractDomainName { luckyecho %s } } ${k} [no url encoding]
  
   **l>**      
This command is a shorter version of the "lucky>" command. It allows you to do a Google "I'm Feeling Lucky" search with the ability to use one set of search terms to desribe the site, and a separate set of search terms to find the item within the site. It is useful if you want to search within a specific site, but you don't know the URL or Yubnub command for that site. NOTES This command uses Allen Ormond's "param" command. Inspired by Eliazar Parra's > and luckyecho commands, that latter of wh...
     214 uses   -   Created 2006-07-31 14:02   -   Last used 2007-03-16 21:40   -         [Description]("http://yubnub.org/kernel/man?args=l%3E")   -   lucky> {param s;k %s}
  
   **lucky>**      
This command allows you to do a Google "I'm Feeling Lucky" search with the ability to use one set of search terms to desribe the site, and a separate set of search terms to find the item within the site. It is useful if you want to search within a specific site, but you don't know the URL or Yubnub command for that site. NOTES Inspired by Eliazar Parra's > and luckyecho commands, that latter of which uses Sean O'Hagan's scrape command. Thanks, guys. AUTHOR Brian Armknecht b.a.
     285 uses   -   Created 2006-07-30 12:42   -   Last used 2007-03-16 21:40   -         [Description]("http://yubnub.org/kernel/man?args=lucky%3E")   -   gfl site:{ extractDomainName { luckyecho %s } } ${k} [no url encoding]
  
   **tru**      
Translate words into/from RUssian language. Thesaurus in RUssian. Supported languages (dictionaries): * (en) English (en-ru, ru-en) * (de) German (de-ru, ru-de) * (fr) French (fr-ru, ru-fr) * (it) Italian (it-ru, ru-it) * (es) Spanish (es-ru, ru-es) * (ru) Russian (ru-ru thesaurus) Without options it translates given non-russian words into Russian, and russian words -- into English (the last one could be customized on the main page). OPTIONS a) Input words are not in Russian: -lang FROM_LANGUAG...
     187 uses   -   Created 2006-07-26 12:45   -   Last used 2007-03-15 17:41   -         [Description]("http://yubnub.org/kernel/man?args=tru")   -   http://lingvo.yandex.ru/{eop search.xml?text=@%s@&st_translate={ifThen (${lang}==ru) 0,1{eop &lang=@${lang}@}}}
  
   **luckyecho**      
Echoes the URL of the first result of googling your keywords. SIMILAR COMMANDS am> (luckyecho is actually a building block for this command) AUTHOR elzr.com Sean O'Hagan's scrape command, as always, was a pleasure to use.
     1074 uses   -   Created 2006-07-24 03:47   -   Last used 2007-03-17 02:46   -         [Description]("http://yubnub.org/kernel/man?args=luckyecho")   -   scrape -tokens class=l href=%22 %22> -dirs 0 0 0 -url {url g %s}
  
   **am>**      
am> is something of a combination of the am command, which searches Amazon.com, and the > one, the "Universal Feeling Lucky command", in that it uses its first %s input to try to uniquely determine a book inside Amazon by googling inside it and selecting the first result. The twist is that it now searches inside that book with the query from the q parameter. Search-Inside-The-Book is a most handy feature of Amazon that allows you to search a book's content and browse through a couple of its pag...
     95 uses   -   Created 2006-07-25 00:37   -   Last used 2007-03-17 02:46   -         [Description]("http://yubnub.org/kernel/man?args=am%3E")   -   http://www.amazon.com/gp/reader/{scrape -tokens ?v= / -dirs 1 1 -url {url luckyecho site:amazon.com %s}}?v=search-inside&keywords=${q}[no url encoding]
  
   **resolution**      
        Description: Type "resolution" (without quotes) to see your computer screen's resolution Example: resolution Author: Troy
     366 uses   -   Created 2006-07-17 20:13   -   Last used 2007-03-16 21:22   -         [Description]("http://yubnub.org/kernel/man?args=resolution")   -   script alert('Your resolution is '+screen.width+'x'+screen.height)
  
   **grazjag**      
A mash-up of Grazr, an OPML browser, and tagjag (formerly gada.be), a OPML content provider. The single argument is the search keyword for tagjag, and the resultant OPML is fed into Grazr for viewing. rickdog - [email]rickfriends@gmail.com[/email] This command gives you an incredibly rich information source for any topic you enter. For example, "grazjag yubnub" will start tge browser on yubnub showing 13 categories at the top level, each category contains feeds for many information sources. For example in the ...
     490 uses   -   Created 2006-07-02 07:03   -   Last used 2007-03-17 07:32   -         [Description]("http://yubnub.org/kernel/man?args=grazjag")   -   [http://grazr.com/gzpanel?font=Tahoma,sans-serif&fontsize=8pt&view=o&file=http%3A//tagjag.com/all/%s/opml](http://grazr.com/gzpanel?font=Tahoma,sans-serif&fontsize=8pt&view=o&file=http%3A//tagjag.com/all/%s/opml)
  
   **argo**      
        Launches the ArgoUML UML design tool via Java WebStart
     115 uses   -   Created 2006-06-28 19:46   -   Last used 2007-02-21 21:02   -         [Description]("http://yubnub.org/kernel/man?args=argo")   -   [http://argouml-downloads.tigris.org/nonav/argouml-0.20/jws/argouml.jnlp](http://argouml-downloads.tigris.org/nonav/argouml-0.20/jws/argouml.jnlp)
  
   **visual**      
JavaScript Visual Wordnet Wordnet is a project at Princeton University that provides a map of the English language. Visual Wordnet presents a visual representation of Wordnet's resources. 
     310 uses   -   Created 2006-06-26 10:51   -   Last used 2007-03-16 21:23   -         [Description]("http://yubnub.org/kernel/man?args=visual")   -   [http://kylescholz.com/projects/wordnet/?%s](http://kylescholz.com/projects/wordnet/?%s)
  
   **wod**      
Who describes better than authors of [www.websters-online-dictionary.org:](www.websters-online-dictionary.org:) What do you get when you start with Websterâ€™s classic 1913 unabridged dictionary, and you add updated definitions, thousands of images (one picture being worth a thousand wordsâ€¦), quotes, trade names, references, timelines, translations and any other bit of information that can help someone understand a word from as many perspectives as possible? For any given word, what you get is Websterâ€™s Online Dictionary with Mu...
     359 uses   -   Created 2006-06-20 13:09   -   Last used 2007-03-16 21:25   -         [Description]("http://yubnub.org/kernel/man?args=wod")   -   [http://www.websters-online-dictionary.org/](http://www.websters-online-dictionary.org/)[post]{IfEmpty -value ${lang} -then {IfEmpty -value %s -then -else search/&s=%s&R1=en} -else {IfEmpty -value %s -then -else search/&s=%s}&R1=${lang}}
  
   **gallery**      
Displays all the jpeg files linked from a page. Give this command an url and it will show all of the images that the url links to. Good for viewing all of the full sized images from a thumbnail page. NOTES This command will not work with all URLs. Some sites will prevent it from working. AUTHOR Allen Ormond - aormond (at) gmail (dot) com
     779 uses   -   Created 2006-06-06 00:38   -   Last used 2007-03-15 10:13   -         [Description]("http://yubnub.org/kernel/man?args=gallery")   -   [http://yubscripts.ning.com/gallery.php?url=%s](http://yubscripts.ning.com/gallery.php?url=%s)
  
   **save**      
         Takes your link and echos a hyperlink in which you can right click to save the target. Jake magicjj jjefferydesign.com
     631 uses   -   Created 2006-06-04 01:18   -   Last used 2007-03-15 19:52   -         [Description]("http://yubnub.org/kernel/man?args=save")   -   echo <a href="%s">Right click, then &quot;Save Target As ...&quot; (IE) or &quot;Save Link As ...&quot; (FF). </a>
  
   **delplaymp3**      
delplaymp3 - stream an mp3 using the del.icio.us PlayTagger (more info here: [http://del.icio.us/help/playtagger](http://del.icio.us/help/playtagger)) This command will load a page that has a play button that lets you stream an mp3 and tag it in del.icio.us Usage: delplaymp3 [url of mp3] example: delplaymp3 http://www.nogu-svelo.ru/songs/SBS9.mp3 author: chicagosage b.a. 
     145 uses   -   Created 2006-02-14 17:34   -   Last used 2007-03-15 17:09   -         [Description]("http://yubnub.org/kernel/man?args=delplaymp3")   -   echo <script type="text/javascript" src="http://del.icio.us/js/playtagger"></script><a href="%s">%s</a>[no url encoding]
  
   **wpm**      
        Wikipedia page suitable for mobile SMS. Thanks to Allen Ormond.
     293 uses   -   Created 2006-05-17 02:09   -   Last used 2007-03-16 14:14   -         [Description]("http://yubnub.org/kernel/man?args=wpm")   -   [http://yubscripts.ning.com/yn-wikipedia.php/.txt?xn_auth=no&length=160&input=%s](http://yubscripts.ning.com/yn-wikipedia.php/.txt?xn_auth=no&length=160&input=%s)
  
   **s.i**      
        Super Image Search Google Images / Yahoo Images / Flickr >||;)
     1429 uses   -   Created 2006-04-16 01:04   -   Last used 2007-03-17 19:00   -         [Description]("http://yubnub.org/kernel/man?args=s.i")   -   split {url[no url encoding] gim %s} {url[no url encoding] yim %s} {url[no url encoding] flickr %s}
  
       Pages:            1 [2]("http://yubnub.org/kernel/golden_eggs?page=2") [3]("http://yubnub.org/kernel/golden_eggs?page=3") [4]("http://yubnub.org/kernel/golden_eggs?page=4") [5]("http://yubnub.org/kernel/golden_eggs?page=5") [6]("http://yubnub.org/kernel/golden_eggs?page=6") [7]("http://yubnub.org/kernel/golden_eggs?page=7") [8]("http://yubnub.org/kernel/golden_eggs?page=8") [9]("http://yubnub.org/kernel/golden_eggs?page=9") [10]("http://yubnub.org/kernel/golden_eggs?page=10") [11]("http://yubnub.org/kernel/golden_eggs?page=11")    [**Next**]("http://yubnub.org/kernel/golden_eggs?page=2")
[http://yubnub.org/kernel/golden_eggs?args=](http://yubnub.org/kernel/golden_eggs?args=)

---

### Post by RAV TUX on 2007-03-18
my favorite YubNub command prompt I just made the other day for work:

```
ncl
```

which is only for windows computers it disables the caps lock function

ncl = No Caps Lock!

see more here
[http://www.ubuntuforums.org/showthread.php?t=385219](http://www.ubuntuforums.org/showthread.php?t=385219)

---

### Post by finferflu on 2007-03-18
One of the commands I use the most, and which I have created myself (yes I'm proud of it) is:

```
glx <query>
```

It searches for items in Google Linux ;)

---

### Post by EdThaSlayer on 2007-03-18
I read a *bit* of that and it does sound like a pretty cool idea to me.  :)
It was a bit stranger than I thought, but then again, the name YubNub is strange by itself.

---

### Post by RAV TUX on 2007-03-18
> **finferflu said:**
> One of the commands I use the most, and which I have created myself (yes I'm proud of it) is:

```
glx <query>
```It searches for items in Google Linux ;)that is awesome!

---

### Post by finferflu on 2007-03-18
Ah, by the way, to enjoy the full advantage of having a command line search engine, you gotta know the key Firefox shortcut for the search bar, so that YubNub really makes sense:

CTRL+K 

moves the cursor on the search bar, and if your default is YubNub, you can start searching whatever you want without even touching the mouse. It makes everything quicker, that's why I find it very very useful.

---

### Post by LookTJ on 2007-03-18
I created 

dpim, ubcfo, pcbsdfo, and pbidir.

---

### Post by RAV TUX on 2007-03-18
> **Taylor said:**
> I created 

dpim, ubcfo, pcbsdfo, and pbidir.where do those go?

---

### Post by LookTJ on 2007-03-19
> **RAV TUX said:**
> where do those go?use man <command> to find out ;)

---

### Post by pbw on 2007-06-06
Almost all of these (if not all), either exist or can easily be created in konqueror (as well as firefox). It's one of the reasons I cant use anything other than konqueror. Maybe i'm missing something, but i fail to see the point. Perhaps someone can show me the difference.

I know not everyone uses konqeuror (though they might if they got accustomed to some of the powerful features like this one), but like i said. firefox can behave like konq and do this too. 


-- pbw

---

### Post by RAV TUX on 2007-06-06
> **pbw said:**
> Almost all of these (if not all), either exist or can easily be created in konqueror (as well as firefox). It's one of the reasons I cant use anything other than konqueror. Maybe i'm missing something, but i fail to see the point. Perhaps someone can show me the difference.

I know not everyone uses konqeuror (though they might if they got accustomed to some of the powerful features like this one), but like i said. firefox can behave like konq and do this too. 


-- pbw[http://jonaquino.blogspot.com/2005/06/yubnub-my-entry-for-rails-day-24-hour.html](http://jonaquino.blogspot.com/2005/06/yubnub-my-entry-for-rails-day-24-hour.html)

---

### Post by pbw on 2007-06-07
Thanks rav, however that didn't explain what i was wondering.

Quick example based on his from that page.

In konq address bar enter ```

ggi:porsche 911

```
For google image search.

---

### Post by RAV TUX on 2007-06-07
> **pbw said:**
> Thanks rav, however that didn't explain what i was wondering.

Quick example based on his from that page.

In konq address bar enter ```

ggi:porsche 911

```For google image search.


ok your at a University library and away from the Konq, how is konq going to help you?



You go to YubNub

---

### Post by pbw on 2007-06-07
Gotcha, i see your point. Makes sense, i didn't think of it that way as each computer i use, be it home or away from home runs linux.

Was just trying to point out that there's a couple native apps that already do all of this. Figured some might not be aware. I'm just so used to it i cant use a browser without it. Always find myself trying to type short commands.

---

### Post by RAV TUX on 2007-06-07
> **pbw said:**
> Gotcha, i see your point. Makes sense, i didn't think of it that way as each computer i use, be it home or away from home runs linux.

Was just trying to point out that there's a couple native apps that already do all of this. Figured some might not be aware. I'm just so used to it i cant use a browser without it. Always find myself trying to type short commands.

I knew about the konq command prompts but never used them, got a short howto or link?

---

### Post by pbw on 2007-06-07
I don't know of a howto offhand. I know there's one to get those functions rockin' in firefox. I can find that for you.. It's less intuitive though.

For konqueror, just click settings -> configure konqueror -> web shortcuts, and you'll see a ton of premade ones you can take a glance at as examples, or edit.

I believe there's a bunch of user contributed ones on kde-apps or something similar. Not 100% on where though.

I don't mind posting a few i created as well for some examples.

---

### Post by RAV TUX on 2007-07-23
> **pbw said:**
> Almost all of these (if not all), either exist or can easily be created in konqueror (as well as firefox). It's one of the reasons I cant use anything other than konqueror. Maybe i'm missing something, but i fail to see the point. Perhaps someone can show me the difference.

I know not everyone uses konqeuror (though they might if they got accustomed to some of the powerful features like this one), but like i said. firefox can behave like konq and do this too. 


-- pbwYubNub command prompts can be used on any computer with internet access.

---

### Post by ice60 on 2007-07-24
i was just looking at it and it's really good :D

i found this bash script -
[http://www.yubnub.org/yubnub.sh](http://www.yubnub.org/yubnub.sh)

you can probably make it in to an alisas :)

---

### Post by RAV TUX on 2007-07-24
> **ice60 said:**
> i was just looking at it and it's really good :D

i found this bash script -
[http://www.yubnub.org/yubnub.sh](http://www.yubnub.org/yubnub.sh)

you can probably make it in to an alisas :)

Cool.

---

### Post by finferflu on 2007-07-27
Very nice one :D

---

### Post by RAV TUX on 2007-07-30
Heres a great command prompt:

[CENTER] ```
"
```[/CENTER]

---

### Post by RAV TUX on 2007-08-09
> **RAV TUX said:**
> Heres a great command prompt:

[CENTER] ```
"
```[/CENTER]


Here is a list of some custom command prompts:

```
c
```= [http://cafelinux.org/](http://cafelinux.org/)

as stated above:
```
"
```= [http://Distropedia.com/](http://Distropedia.com/)

```
}
```= [http://OptickleArt.com/](http://OptickleArt.com/)

```
(
```= [http://LinuxNirvana.com/](http://LinuxNirvana.com/)

```
)
```= [http://OzEnterprise.com/](http://OzEnterprise.com/)

Thats all I can think of right now ;)

---

