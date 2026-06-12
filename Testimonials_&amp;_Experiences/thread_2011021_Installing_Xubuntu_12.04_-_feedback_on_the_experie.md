---
title: "Installing Xubuntu 12.04 - feedback on the experience"
date: 2012-06-26
forum: Testimonials &amp; Experiences
---

### Post by curaga on 2012-06-26
I installed Xubuntu 12.04 amd64 desktop today on an E-450 laptop (HD, 4gb ram). Here's the feedback on the process.

- it took ages to boot to the installer from CD. A bit over 3 minutes, with huge seeking. I get that USB is the future, but still, the tools to order the compressed blocks exist, to eliminate seeks and greatly speed up CD boots.

- it appears the WM crashed when the installer had started. It's merely my guess, but moving the installer window around left gray behind it, overwriting the nice background picture.

- language packs and restricted items were downloaded against my best guess, as I had unticked the "download updates during installing". Yes, that's not exactly what it says, but there was no tickbox "don't connect to the net during install", and I think there should be.

This is because the default mirror is usually slow, getting 0.5-0.75x the speed of the best mirror, as picked by the automatic mirror tool in synaptic / software sources.

- the installer re-generated the initramfs about 15 times during the install. Slowly. Each time. Hint, just mark it as "needs to be done" and do it once at the end. I estimate one generation took about 8-10sec on this hw, so that's two minutes of install-time wasted by re-generating the initramfs unnecessarily.

- watching the install log go by, there were a huge number of various failures. All non-fatal and expected, I must believe, but still quite ugly to see them there.


Well, that's it for the install experience.

For the installed system I only have one gripe: After bios, the screen is black for 4-5s, then the nice plymouth animation shows up for 1s, then it's lightdm time.

One would think the times of black screen and plymouth animation should be reversed ;)


Signed, a dev of another distro, having installed latest Xubuntu for a family member.

---

### Post by Elfy on 2012-06-26
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by mastablasta on 2012-06-27
> **curaga said:**
>  
- language packs and restricted items were downloaded against my best guess, as I had unticked the "download updates during installing". Yes, that's not exactly what it says, but there was no tickbox "don't connect to the net during install", and I think there should be.

 
if you unticked the box "download updates" or whatever it is then it shouldn't download them.

---

### Post by rai4shu2 on 2012-06-30
That's pretty darn good, actually. My experience with Ubiquity is usually worse than that. I usually get at least one crash right before it goes to install grub (leaving me with a system I have to fix by hand).

---

