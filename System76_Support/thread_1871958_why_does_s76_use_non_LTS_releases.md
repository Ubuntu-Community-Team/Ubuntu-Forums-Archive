---
title: "why does s76 use non LTS releases"
date: 2011-10-29
forum: System76 Support
---

### Post by moldaviax on 2011-10-29
Hi
I was wondering what motivates S76 to focus upon supporting the latest ubuntu releases? Doesn't this generate an awful lot of teething trouble for the S76 team every few months?
M.

---

### Post by jml on 2011-10-30
I am not a S76 employee, but my guess is that that is what their market research shows the majority of their customers want.  When an LTS release is the current one, they install that version on the laptops they sell.  Personally, on most of my System 76 hardware, I run Debian stable.  A really LTS distro.

Joe

---

### Post by Eldera on 2011-10-30
I am not a S76 employee either, but I seem to recall a couple of posts where S76 stated that they were trying to offer cutting edge hardware and and not all of it would work with Lucid 10.04LTS

---

### Post by 3Miro on 2011-10-31
I just got a new Pangolin and the video will not run on anything before kernel 2.6.37, this means that both 10.04 and 10.10 are out of the picture.

---

### Post by stangdaman on 2011-10-31
Really? My Pangolin, which was purchased a while ago, is running 10.04 LTS and doesn't seem to have any video issues. I probably won't update until the next LTS comes out.

---

### Post by 3Miro on 2011-11-01
> **stangdaman said:**
> Really? My Pangolin, which was purchased a while ago, is running 10.04 LTS and doesn't seem to have any video issues. I probably won't update until the next LTS comes out.

Which one did you get. I have the one with Sandy Bridge Intel HD 3000 graphics. When those chips first came out, there were many problems with the drivers and only recent versions of the kernel and Xorg have fixed those.

If you have a model with ATI or older Intel graphics, you wouldn't have any issues on the LTS release.

---

### Post by stangdaman on 2011-11-01
Yeah, that's the one I have. I have the ATI 4570 model.

---

### Post by 3Miro on 2011-11-01
> **stangdaman said:**
> Yeah, that's the one I have. I have the ATI 4570 model.

The ATI 4xxx series came out before 10.04 was released, so 10.04 does have proper drivers. Sandy Bridge came out right around the same time as 10.10 and Intel had dropped with ball with the first batch of drivers that just weren't working right. If you have the newer Intel graphics, you have to use kernel 2.6.37 or newer (Ubuntu 11.04 or newer).

---

### Post by Flyers2391 on 2011-11-01
Perhaps things are changing in regards to the LTS releases.  I just came across this when browsing on ubuntu.com: [http://www.canonical.com/content/ubuntu-1204-feature-extended-support-period-desktop-users](http://www.canonical.com/content/ubuntu-1204-feature-extended-support-period-desktop-users)

> The first two years of the LTS period will benefit businesses by including hardware updates (through regular point releases) allowing them to keep up to date with the latest hardware upgrades.

Does that mean that new chipsets released during the first 2 years of a (now support with 5 years of maintenance updates) LTS release will be supported?  If so, System76 could offer the latest LTS at all times, and a second option of the latest release ... that would be a great comprise for both sides of the argument.  

Of course, that assumes "hardware updates" means what I'm hoping it does :D

---

### Post by isantop on 2011-11-03
> **stangdaman said:**
> Yeah, that's the one I have. I have the ATI 4570 model.

That's the PanP7, which uses first-gen iX processors. The new PanP8 that we sell now uses integrated Sandy Bridge graphics from the second-gen Intel processors, which aren't supported at all prior to Natty.

We want to offer the most cutting-edge hardware experience required, so we often need the latest release to make it work. Some things simply won't run on an older kernel.

---

### Post by moldaviax on 2011-11-04
cheers isantop, that clears things up for me :)

M.

---

