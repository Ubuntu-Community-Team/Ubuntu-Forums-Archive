---
title: "Does anyone have any sort of guide to releasing open source software?"
date: 2010-08-13
forum: Ubuntu Dev Link Forum
---

### Post by Vunutus on 2010-08-13
I have a little piece of PHP software I intend to make public soon. It isn't massively complex as it is but I intend to improve on it in subsequent versions. I mean, sure I can just shove it out there and call it good, but I'm  wanting to know more specifics such as:

1. How to choose the right license. I want my code to be free in both senses of the word but I also want to have some sort of authority over the project

2. How to make the license information available. I know the LICENSE file in distributable packages is fairly common but what about license information as comments in source files? Is this required or just a "nice to have" thing?

3. How to deal with bundled libraries and their respective licenses. My project bundles two libraries built by other people which I believe are both GPL'd. Do I need to do anything special to redistribute them?

Also, as a tagalong question to this topic, does anyone have any resource about how to handle version numbering? Right now it feels like I'm just pulling version numbers out of my butt and I'd like some more concrete scheme to follow.

In other words, I have questions about pretty much everything *except* the actual code :D

EDIT: Wow this ended up in the wrong forum somehow. I'd appreciate it if a mod could move this to programming talk :D

---

### Post by RainCT on 2010-08-22
1. That's up to you. Personally I usually use the GPLv3+ (which is a copyleft license and has an important focus on the user's freedom), except for little things I don't really care about which I may release under the more liberal (eg. it allows making stuff closed-source) ISC license. Google can give you some more detailed articles with the differences between many popular licenses.

What do you mean by "have some sort of authority"?

2. That depends on the license you choose. If it's a short one (eg. ISC/MIT/BSD) it's common practice to include it completely in every file header, if it's a longer text then use a reduced header pointing to the license (in the case of the GPL, it has a standard header for this which you'll find at the end of the license) and including a LICENSE/COPYING file with the full copy.

Having a license header in all files helps reduce concerns about what falls under which license and what not. I also recommend stating the copyright information for each file in the header ("Copyright (c) YEAR NAME <EMAIL>" is the usual format).

As on whether it's required to included a full copy of the license in the tarball, that depends on the particular license but most often the answer is yes. In any case, it certainly won't hurt.

3. Please, don't bundle libraries. You'll only make distributor's life more difficult since they'll have to remove them anyway and have your software use the system's libraries.

4. About the version numbering, just use something sane like for example 0.1/1.0/1.2.3. Things you should avoid are underscores (_), plus signs (+) and tildes (~), since those have a special meaning.

Also, 0.1 is not the same as 0.10, the later is a higher version number. And don't do stuff like "0.1beta1" if you don't want to end in hell ;). I've just told you not to use tildes, but this is a case where you should actually use them, turning your version number to "1.0~beta1", since the tilda means "previous to" (so, this makes "1.0~beta1" a smaller version than "1.0"). Or just don't use the word "beta" and make "0.90" out of it instead.

---

### Post by stevebu56 on 2010-09-07
This is a good resource.  Although a little old, a lot of it is still relevant. 

[Eric Raymond-Software-Release-Practice-HOWTO]("http://en.tldp.org/HOWTO/Software-Release-Practice-HOWTO/")

---

### Post by juancarlospaco on 2010-09-17
I usually use GPLv3, or WTFPL at least.

---

