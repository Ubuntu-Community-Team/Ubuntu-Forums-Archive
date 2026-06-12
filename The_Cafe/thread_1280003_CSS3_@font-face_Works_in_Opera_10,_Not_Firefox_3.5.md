---
title: "CSS3 @font-face Works in Opera 10, Not Firefox 3.5, 3.6, 3.7, or Swiftfox?"
date: 2009-10-01
forum: The Cafe
---

### Post by moore.bryan on 2009-10-01
Perhaps a little help, folks... I've declared an @font-face on the website for my class ([http://www.bmoore.net/](http://www.bmoore.net/)) and everything's showing-up fine in Opera 10, but no love in the other browsers. Huh? What gives?

---

### Post by Tibuda on 2009-10-01
Firefox supports it, but it is different from Opera. IE is even worse, as it uses a different file format.

This blog post explains some workarounds to get it working cross-broswer: [http://randsco.com/index.php/2009/07/04/p680](http://randsco.com/index.php/2009/07/04/p680)

EDIT: ImpactLabelReversed is the font you are embedding? I think it is working here in FF3.5, as your header got a different font.

---

### Post by moore.bryan on 2009-10-01
> **danielrmt said:**
> Firefox supports it, but it is different from Opera. IE is even worse, as it uses a different file format.
Yeah, this I know. What I'm saying is Opera *works*, but FF doesn't.
> 
This blog post explains some workarounds to get it working cross-broswer: [http://randsco.com/index.php/2009/07/04/p680](http://randsco.com/index.php/2009/07/04/p680)

Read this over and over and did everything it suggested; am I missing something?
> 
EDIT: ImpactLabelReversed is the font you are embedding? I think it is working here in FF3.5, as your header got a different font.
Strange... not working here. I know this is a **long** shot, but could the proxy I'm currently behind cause the "remote" font not to be loaded?

EDIT:
Alright... now I'm *really* confused; it's working on everything now! I just spent about an hour trying to get it to work and nothing... now, Opera 10, Swiftfox 3.5.3, Shiretoko, and Minefield all display it properly. WTF?

---

### Post by Tibuda on 2009-10-01
> **moore.bryan said:**
> Strange... not working here. I know this is a **long** shot, but could the proxy I'm currently behind cause the "remote" font not to be loaded?

Maybe, if this is the case, try testing in a local server. But I don't think this is the case if it is working with Opera.

---

### Post by Tibuda on 2009-10-02
> **moore.bryan said:**
> EDIT:
Alright... now I'm *really* confused; it's working on everything now! I just spent about an hour trying to get it to work and nothing... now, Opera 10, Swiftfox 3.5.3, Shiretoko, and Minefield all display it properly. WTF?

Perhaps *fox got your CSS cached before you added the @font-face.

---

### Post by DragonFlyEye on 2010-12-31
> **moore.bryan said:**
> Strange... not working here. I know this is a **long** shot, but could the proxy I'm currently behind cause the "remote" font not to be loaded?

Short answer is yes, caching on the server side can definitely cause wonkiness with fonts. My company has been playing around with a custom printing application that allows users to apply @font-face derived fonts to their finished products. When we did this, we discovered that caching on the server affected whether or not the file was downloaded. This was an IIS system, but it's reasonable to assume that Apache might have similar complications.

I'd say turn off all server-side caching directives and see if that changes anything.

---

