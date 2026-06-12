---
title: "would this browser addon be possible/practical?"
date: 2010-07-06
forum: The Cafe
---

### Post by Dustin2128 on 2010-07-06
I recently read a post in one of those anti-IE threads that gave me an idea for an addon for firefox or IE that could help immensely with web standards-compliance. Say a visitor to your site is using internet explorer, but instead of it appearing completely broken (20/100 acid 3 compliance :shock:), a bit of code in the site gives the visitor a dialogue telling them 'this site renders best in chromium', giving a choice to open a tab that uses the chromium layout engine. I'm pretty sure it's possible, my only concerns are speed, and required amount of coding. I think it'd be amazing if it could be done, imagine only having to develop a website for one compatible browser and have it work for all!

---

### Post by undecim on 2010-07-07
Well, for starters, you would need to either

1: get everyone using the add-on (anyone who knows enough to get the addon will use a descent compliant browser anyways)
2: get all major browsers to have it preinstalled (hint: MS won't EVER do that)

So, there really is no practical way to do this so that you would only have to check one browser's rendering.

Although for Firefox Windows users, there is the IE Tab plugin which lets you run IE inside firefox with the click of a button.

---

### Post by Dustin2128 on 2010-07-07
> **undecim said:**
> Well, for starters, you would need to either

1: get everyone using the add-on (anyone who knows enough to get the addon will use a descent compliant browser anyways)
2: get all major browsers to have it preinstalled (hint: MS won't EVER do that)

So, there really is no practical way to do this so that you would only have to check one browser's rendering.

Although for Firefox Windows users, there is the IE Tab plugin which lets you run IE inside firefox with the click of a button.

Of course, there are those who can't swap browsers due to only being allowed to have IE installed at work/school. That's more the market I'm targeting here.

---

### Post by v1ad on 2010-07-07
at times in those cases, they won't even be able to install the plugin.

---

### Post by Madspyman on 2010-07-07
Most modern browsers (Chrome, Firefox, Opera) render pretty similarly, it's really IE you have to worry about. You could always create an IE specific style sheet, even make it so the only thing IE users see is "your browser is outdated, in order to view this site please install [google's chrome frame plugin]("http://code.google.com/chrome/chromeframe/") and restart your browser."

As long as you have the proper code on your website IE users won't see that message again after chrome frame has been installed.

---

### Post by lucyburnett on 2010-07-07
There might be some few people who might want this but if you thinking about profiting from it then you will most likely find the market being too thin/small for that. But, your idea is certainly good.

---

### Post by Paqman on 2010-07-07
Eugh! Browser sniffing should be left back in 1995 where it belongs. Just build sites that render properly on IE. It's a pain, but it's got to be done. 

Microsoft's slackness about web standards and the misery it causes web designers is not your visitor's problem.

---

### Post by Madspyman on 2010-07-07
> **Paqman said:**
> Eugh! Browser sniffing should be left back in 1995 where it belongs. Just build sites that render properly on IE. It's a pain, but it's got to be done. 

Microsoft's slackness about web standards and the misery it causes web designers is not your visitor's problem.

IE9 will support html5 but will only be for Win7/Vista, that leaves anyone using IE in XP out of the loop. Fallback support isn't available for all of the html5 options. 

I think users have the right to know they have better browser options, also offering a plugin like chrome frame as an alternative would mean they could keep using their default browser, its no different than having to install Flash, except it's a better alternative.

Things need to move forward, even if it takes some sniffing around to get it done.

---

### Post by Paqman on 2010-07-07
> **Madspyman said:**
> 
I think users have the right to know they have better browser options

They probably do. But what they want more is for the page to load.

Back in the bad old days of the net, sites always used to throw up all sorts of bumf about which version of which browser you should be using to view it. These days browser sniffing is frowned upon, as the required workarounds to get any page working in IE are well documented.

The bottom line is that the users who stand the most to gain from updating/switching their browser are also the ones who don't really care about it. And to be fair, would YOU install a new browser just because one site told you to, when every other site on the net just got on with it?

---

### Post by Madspyman on 2010-07-07
> **Paqman said:**
> They probably do. But what they want more is for the page to load.

Back in the bad old days of the net, sites always used to throw up all sorts of bumf about which version of which browser you should be using to view it. These days browser sniffing is frowned upon, as the required workarounds to get any page working in IE are well documented.

The bottom line is that the users who stand the most to gain from updating/switching their browser are also the ones who don't really care about it. And to be fair, would YOU install a new browser just because one site told you to, when every other site on the net just got on with it?

Ever been to Youtube in IE6? Or maybe tried some of Google's apps? You get an unsupported browser message, with upgrade options. Even Hulu has an upgrade your browser message up.

I'm not against providing a working site for IE6/7 it's easy to do with css, but even Google is sniffing around making sure they can move into the future. There's a precedent for it.

Also offering chrome frame as a necessary plugin is not really any different than having to install Flash, Java, or any number of Activex plugins, IE users should be used to it.

---

### Post by Paqman on 2010-07-07
> **Madspyman said:**
> Ever been to Youtube in IE6? Or maybe tried some of Google's apps? You get an unsupported browser message, with upgrade options. Even Hulu has an upgrade your browser message up.


There's a world of difference between encouraging IE users to upgrade to a newer version of IE, and telling them to switch browsers.

---

### Post by Madspyman on 2010-07-07
The upgrade message Google offers also suggests other browsers to upgrade to. Also I keep throwing the chrome frame plugin out there, that doesn't even require a full browser upgrade, it's a plugin like Flash.

Point is offer the upgrade/switch option with the option to keep the current browser and use a plugin to correctly view the content.

---

### Post by Mr. Picklesworth on 2010-07-07
Just take gracefully degrading CSS as a personal challenge!
(And don't worry; you can have IE5+-specific CSS using the <!--[if lte IE 6]> trick).

It doesn't need to look the same in IE6. Those folks probably won't care if a web site looks uglier than it should (and if they do, you're sending them a valuable message), but it isn't that hard to make it work.

---

### Post by Dustin2128 on 2010-07-07
Well this is mainly for business websites (I don't plan to make a profit; this is a side project more or less) because on my personal website I have an IE redirect with an option to continue. I don't want to waste my time coding for IE, and I don't want to leave out HTML5, so I don't. The majority of my visitors are firefox or linux users anyway though, whereas I have to spend quite a lot of time hacking business websites I design to work for IE.

---

