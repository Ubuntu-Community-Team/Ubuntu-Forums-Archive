---
title: "Anyone want to help make a Paint.Net alternative for Linux?"
date: 2009-07-13
forum: The Cafe
---

### Post by keiichidono on 2009-07-13
I really miss Paint.Net in Windows for simple image editing without complex controls. There's a Mono port that can be used as a reference but I think it should be coded in something other than C# and Mono....in any case I can do the web design/developing for the website though that might not be necessary. Just looking to see if anyone would be interested in doing the project.

---

### Post by UbuWu on 2009-07-13
You might be interested in [Nathive]("http://www.nathive.org/"). It does pretty much what you describe and has recently been rewritten in python. It is still in an early stage, and I certainly think their website can use a good web designer's helping hand.

---

### Post by twright on 2009-07-13
> **CalvinB said:**
> I really miss Paint.Net in Windows for simple image editing without complex controls. There's a Mono port that can be used as a reference but I think it should be coded in something other than C# and Mono....in any case I can do the web design/developing for the website though that might not be necessary. Just looking to see if anyone would be interested in doing the project.
Why not C# and Mono? As long as the interface is rewritten in Gtk# rather than WinForms it would feel completely native.

---

### Post by zekopeko on 2009-07-13
> **CalvinB said:**
> I really miss Paint.Net in Windows for simple image editing without complex controls. There's a Mono port that can be used as a reference but I think it should be coded in something other than C# and Mono....in any case I can do the web design/developing for the website though that might not be necessary. Just looking to see if anyone would be interested in doing the project.

Your right! Let's re-write the entire application! Why re-use code? It's not like it's an integral part of FOSS and it's greatest advantage.

---

### Post by phrostbyte on 2009-07-13
Yeah it would probably be a lot easier to port Paint.NET to Linux then rewrite it from scratch. Especially considering there is already a project porting it. :)
[URL="http://code.google.com/p/paint-mono/"]
http://code.google.com/p/paint-mono/[/URL]

Apparently most of the work porting Paint.NET to Mono is writing a replacement for a single library (that platform invokes Win32 APIs).

---

### Post by dragos240 on 2009-07-13
> **phrostbyte said:**
> Yeah it would probably be a lot easier to port Paint.NET to Linux then rewrite it from scratch. Especially considering there is already a project porting it. :)
[URL="http://code.google.com/p/paint-mono/"]
http://code.google.com/p/paint-mono/[/URL]

I tried that a while ago, it worked, but the text was messed up, now I can't get it to compile at all :(

---

### Post by keiichidono on 2009-07-13
I don't care what the Ubuntu and Gnome devs say, I agree with rms. Mono is very bad. Nathive is cool, but not yet where I want it to be. I could support him though I'd need to know his roadmap.

[http://pastebay.com/29187](http://pastebay.com/29187)

---

### Post by phrostbyte on 2009-07-13
I got it to compile. Ubuntu 9.04

I just used: ./configure; make; sudo make install
I have most of Mono installed

It works alright, it's a bit slow though.

Here is a fast install (copy/paste this into a Terminal):
Disclaimer: This probably won't screw up your computer, but all risks are possible :)
---------------------------------------------------------------------------------------

```

sudo apt-get install subversion libmono-* mono-* build-essential
svn checkout [http://paint-mono.googlecode.com/svn/trunk/](http://paint-mono.googlecode.com/svn/trunk/) paint-mono-read-only  
cd paint-mono-read-only/src
./configure
make
sudo make install
paintdotnet

```

---

### Post by Simian Man on 2009-07-13
> **CalvinB said:**
> I really miss Paint.Net in Windows for simple image editing without complex controls. There's a Mono port that can be used as a reference but I think it should be coded in something other than C# and Mono....in any case I can do the web design/developing for the website though that might not be necessary. Just looking to see if anyone would be interested in doing the project.

So basically you want somebody else to write an application for you in the language and design of your choosing.  And all you're contributing a website?  Seriously?

---

### Post by phrostbyte on 2009-07-13
> **Simian Man said:**
> So basically you want somebody else to write an application for you in the language and design of your choosing.  And all you're contributing a website?  Seriously?

Yeah that's not going to work out. I know some people don't have programming experience and can't really judge the difficulty of certain software projects. It's A LOT of work to write a image editor, even one not as powerful as Photoshop. I'm pretty sure PaintDotNet is something like hundred thousand lines of code. If you printed it out you'd probably need 10 reams of paper. :) I don't have the source code of The GIMP, but I bet it's even bigger considering it's written in C and needs more code for memory management and the like.


Image editor = NOT EASY! This isn't a pong clone. :)

It involves knowing high level mathematics too. Like **above** undergraduate level Calculus! (Think DiffEq and Advanced Linear Algebra)

---

### Post by keiichidono on 2009-07-13
> **Simian Man said:**
> So basically you want somebody else to write an application for you in the language and design of your choosing.  And all you're contributing a website?  Seriously?

I was thinking people would want a mono alternative to PDN Mono and would be interested in developing something. I'm not asking for money or food, I'm asking if anyone wants to join the **PROJECT** and make it happen. **** it if everyone is gonna be an ******* about it. =\

---

### Post by dragos240 on 2009-07-13
> **CalvinB said:**
> I was thinking people would want a mono alternative to PDN Mono and would be interested in developing something. I'm not asking for money or food, I'm asking if anyone wants to join the **PROJECT** and make it happen. **** it if everyone is gonna be an ******* about it. =\

What kind words you posses.

---

### Post by zekopeko on 2009-07-13
> **CalvinB said:**
> I was thinking people would want a mono alternative to PDN Mono and would be interested in developing something. I'm not asking for money or food, I'm asking if anyone wants to join the **PROJECT** and make it happen. **** it if everyone is gonna be an ******* about it. =\

code == money == food. so you see you are asking for money and food.

btw your whole "mono is bad" stance comes from a 20min IRC conversation with 10year old "evidence". perhaps proper education on the subject would alleviate the fears you have?

---

### Post by jonian_g on 2009-07-13
> **zekopeko said:**
> code == money == food. so you see you are asking for money and food.

btw your whole "mono is bad" stance comes from a 20min IRC conversation with 10years old "evidence". perhaps proper education on the subject would alleviate the fears you have?

Is there any post that mentions mono and you haven't answered to?

You're f*****g annoying! I believe everyone has got your point about mono. This thread is not about mono, it is about a Paint.Net alternative.

---

### Post by twright on 2009-07-13
If Microsoft wanted to sabotage Linux they would start by creating blog posts/IRC conversations/flamewars about how evil mono is :-) (and it would work)

Seriously most of the rubbish you hear about mono is just that, rubbish. I could go through refuting each point in the conversation but that would be a complete waste of time. Basically the best way to port paint.net to Linux is contributing to the C# port, I'm sure they would not mind a web designer on the team. You are not going to convince any programmer to rewrite a massive graphics application in C/C++ (which arguably are worse languages for the job) just because you have a personal disliking to Mono - the Gimp took 15 years and a massive community of extremely talented contributors to write.

In the conversation you list gnote as an example and I think it is an extremely good example of why **not**to rewrite existing applications in a different 'just because you can'; it looses all of the momentum behind the original program whilst alienating its community. Gnote in short was a waste of time but as note-taking is fairly simple it was a small one - rewriting a full on graphics application like paint.net would be a colossal waste of time.

---

### Post by zekopeko on 2009-07-13
> **jonian_g said:**
> Is there any post that mentions mono and you haven't answered to?

You're f*****g annoying! I believe everyone has got your point about mono. This thread is not about mono, it is about a Paint.Net alternative.

you're right! so the easiest (and closest to paint.net) solution is to port paint.net to linux (and mac) with the gtk# UI.

P.S. would you tell me if i missed any mono threads? my OCD demands that i post in each one.

EDIT: twright beat me to the punch!

---

### Post by dragos240 on 2009-07-13
I just compiled the lastest subversion build, using the post phrostbyte. It works flawlessly!

---

### Post by twright on 2009-07-13
I would not mind coding (parts of) a gtk# UI myself if/when I have some more time/c# experience :KS . See, we are not just all Mono loving nuts in the pay of Microsoft.

---

### Post by zekopeko on 2009-07-13
> **twright said:**
> I would not mind coding (parts of) a gtk# UI myself if/when I have some more time/c# experience :KS

awesome! This could expand paint.net(.mono) to a multitude of platforms.

---

### Post by twright on 2009-07-13
> **zekopeko said:**
> awesome! This could expand paint.net(.mono) to a multitude of platforms.
No promises :-) . It already works quite well using WinForms (it does not really look native but then again it does not look great on Windows either) and I think that I would need to learn a lot more gtk# before I would be much use. Still if the project gets underway or I am ever particularly bored I will at least have a look.

---

### Post by cariboo on 2009-07-13
THis thread seems to have degenerated into name calling. This thread is closed.

---

