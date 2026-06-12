---
title: "No Nonsense Development Enviroment"
date: 2008-05-05
forum: Repositories &amp; Backports
---

### Post by docmarine on 2008-05-05
I am looking for a simple **guide** to *installing* and *maintaning* a development enviroment with the following requirements:

[LIST=1]
[*]Ubuntu 8.04
[*]NetBeans 6.1
[*]Ruby
[*]Ruby on Rails
[*]mySQL
[*]apache
[*]SSL
[/LIST]

   I am looking for the simplest solution possible, I have no problem using XAMPP, etc.

I understand that there are several tutorials strewn about the interweb on this topic... What I I am really asking for is a "tried and true" guide to making this happen... while keeping the maintenance headache to a minimum

 I am not really a noob, but I'm not all that experienced either (so treat me like one please ;) ). I have **many** new web projects that i want to begin working on.. i just wanna get down to coding! Thanks in advance.

---

### Post by Jordanwb on 2008-05-05
Well if you have no problem with XAMPP then that solves #5 and 6. As for SSL which end of the stick are you? Server or client?

---

### Post by docmarine on 2008-05-05
Thanks for your response, Jordanwb. I am going to be the server.... I believe XAMPP has SSL 

... I think in need to be a bit clearer with my XAMPP remark. I meant to say i will have no problem using XAMPP if it is the best way to ensure everything works nicely.

---

### Post by Jordanwb on 2008-05-05
Well on Windows I've never had any problems. I got SSH confused with SSL, my bad.

---

### Post by docmarine on 2008-05-05
Yep... I have a windows laptop that this all works on... I dont want to use it for development..  my main setup is much nicer (3 screens)

---

### Post by Jordanwb on 2008-05-05
You have three monitors? Awesome!

---

### Post by docmarine on 2008-05-06
Yes i do... So any advice with this setup?

---

### Post by Jordanwb on 2008-05-06
Well installing Ubuntu is a good starting point. Installing NetBeans is easy. To install XAMPP download the package from their site and install. I don't know about the setup of Ruby or SSL.

---

### Post by docmarine on 2008-05-06
That much i fugured out... its no problem. Ruby (on Rails) is what;s giving me a hard time... like i mentioned i am looking for a comprehensive guide.

---

### Post by howlingmadhowie on 2008-05-06
> **docmarine said:**
> That much i fugured out... its no problem. Ruby (on Rails) is what;s giving me a hard time... like i mentioned i am looking for a comprehensive guide.

Ruby and Rails are both in the repositories, as are all the other programs you mentioned.

---

### Post by jayk121121 on 2008-05-06
You might want to try either [RubyStack]("http://bitnami.org/stack/rubystack") or [RM-Install]("http://www.fiveruns.com/products/rm/install"). I personally like RM-Install better (I think that there was some issue with the RubyStack installer). RM-Install provides everything you asked for except NetBeans (for that you can easily download the correct installer [here]("http://download.netbeans.org/netbeans/6.1/final/")) and Ubuntu 8.04 (I assume you already have that:)).

---

### Post by docmarine on 2008-05-07
Thanks for the advice... I going to try it out...  Do you have any preference on IDEs... i know that Mac has TextMate(?). What do you prefer, Netbeans, Eclipse, something else?

---

### Post by jayk121121 on 2008-05-10
When I first started using Ubuntu, I just used the plain gedit which came with it. However, I was recently introduced to wonders of emacs. I also conveniently found a [plugin]("http://rubyforge.org/projects/emacs-rails/") for emacs just for rails development. If you decide that you want to use or at least try emacs, then you should install the "emacs" package using your favorite package management tool. Then, after you have opened up the emacs window, press Control-h t (press and hold control and press h, and then let go of everything and press t). That will bring up a tutorial, which will guide you through using emacs. There is also a wiki [here]("http://www.emacswiki.org/cgi-bin/wiki").

---

### Post by jayk121121 on 2008-05-11
If you do not wish to spend much time learning a complex editor like emacs (Although I strongly recommend it), you can make the default gedit act like Text Mate. There are many web pages about that subject, but [here]("http://www.thaumatocracy.com/textpad-for-linux") are two [links]("http://grigio.org/textmate_gedit_few_steps").

---

### Post by jayk121121 on 2008-05-11
There is also an IDE called [EasyEclipse for Ruby and Rails]("http://www.easyeclipse.org/site/distributions/ruby-rails.html"). I have never personally tried it.

---

