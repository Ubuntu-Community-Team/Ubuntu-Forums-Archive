---
title: "Pointers needed for new website."
date: 2009-04-07
forum: The Cafe
---

### Post by Mehashi on 2009-04-07
[COLOR=Magenta]Hi guys[/COLOR]!

Finally, after reading a response from [HermanAB]("http://ubuntuforums.org/member.php?u=44990") (thank you - I did not know where to start either!) I have registered my domain name with the internet gods and have confirmed it to be working and the license good. However I have not yet built my site!

I have basically zero knowledge of web building so I could do with some starting pointers!
I do some graphic design so that might help me a little maybe?

For example:

[LIST]
[*]Good programs to use. (I have Dreamweaver CS3 for windows but nothing for ubuntu)
[/LIST]

[LIST]
[*]Good free ad-free hosts I could link to my domain name. (currently using free host with banner at top)
[/LIST]

[LIST]
[*]Hints or tips that may make things easier to learn or that a newbie may overlook. (remember this is *completely* new to me)
[/LIST]

[LIST]
[*]Anyone who knows about SQL databases. (to point to how to display japanese kanji on my site as the how tos I have read are so confusing and only seem to cover my machine, rather than making it veiwable to others cross-platform)
[/LIST]

I have done a bit of googling but what I am really looking for is services or programs that people trust or have had good experiences with as there is a minefield of people who want to host my site that I do not trust at all (I fortunately read an article warning of hosting scams before looking around)

Also it would be worth noting that I use a mix of ubuntu at home and windows at work with a mix in-between.

Thanks for any help - I appreciate this has nothing to do with ubuntu really but you have all been a source of trusted help for me!

[COLOR=Magenta]Arigato gozaimasu[/COLOR]!
^_^

---

### Post by ddrichardson on 2009-04-08
Servage are OK as hosts, I've used them for years.

I prefer a hosted solution, especially where there are scripts to install common web applications and configure SQL databases. The thing is, I rarely write a page anymore - there's usually a web application that I'm using. Wordpress for blogging, DokuWiki and Drupal on other sites I maintain.

It depends more on what you want your site to do and if you want to develop/work on it cross platform then content management, being web based, is a good start.

As for kanji, it depends. If east asian language support is enabled on a Windows machine or the font is then the web page can suggest the browser uses it and you can tell your readers. If its light kanji then images are a cumbersome but portable option. Ubuntu doesn't have a problem recognising the hiragana on the front of my site [http://www.lynxworks.eu/](http://www.lynxworks.eu/)
but the font isn't anti-aliased and looks better in Windows.

---

### Post by ddrichardson on 2009-04-08
Most browsers also support unicode too, [http://tlt.its.psu.edu/suggestions/international/bylanguage/japanesecharthiragana.html](http://tlt.its.psu.edu/suggestions/international/bylanguage/japanesecharthiragana.html). Putting:
```
<p>& #12353;</p>
```Should display &#12353;. Note you have to remove the space from between the & and the # - I had to put it in there to get it to show the code.

I started learning conversational Japanese fairly recently and as the zenith of my knowledge is "excuse me, do you speak English" I fear I mightn't be able to offer more help on language display than this.

---

### Post by renzokuken on 2009-04-08
i'd recommend HostPapa as a good host.

also, if you have zero knowledge it may be a good idea to get some basic html/php under your belt. [w3schools](http://www.w3schools.com/) is a great place to start

also, there are tons of open source web templates you can freely download and edit/customize to your needs. check out
[www.oswd.org](www.oswd.org)
[www.openwebdesign.corg](www.openwebdesign.corg)

---

### Post by Mehashi on 2009-04-08
[COLOR=Magenta]Thanks guys[/COLOR]! 

I will definately look into unicode to display hirigana, thank you that is really helpful! A lot of guides I have read suggested installing things to get characters to display, but I can not expect people to download something just to see my site! I would not want to either! 

I just checked the link that you gave to me ddrichardson for the unicode characters, and it is EXACTLY what I was looking for!!! Thank you!

Also thanks for providing me with a starting place Renzokuken-san! I will certainly use those links to gain some experience. Thank you!

I really appreciate the help guys, I am not completely useless, it is just hard google searching when I dont know what I should be searching for! I am a fast learner though and will soon get this site running.

As far as content goes it is predominantly tutorials, how-to, guides, hints and tips covering all the things I have encountered. There are sections on travelling, learning another language, science experiments, computer modifications, level design for games, and plenty more. Essentially it is my survival guide to life so far!

Thank you for your help and links!

[COLOR=Magenta]^_^[/COLOR]

---

