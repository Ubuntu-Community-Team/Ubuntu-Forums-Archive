---
title: "intel-mac applications on linux?"
date: 2006-05-23
forum: The Cafe
---

### Post by kapetanski on 2006-05-23
Just wondering if it's possible to run mac applications (universal binary) on linux, or how hard it's to port them over to linux. As they both are build upon unix, is it possible to recompile or something like that? I've heard many uses wine to run windows apps, but to me it seems better to run osx apps on linux.

---

### Post by mostwanted on 2006-05-23
It's not easy. That they're bot *NIX doesn't really mean that much because of these factors:

[LIST]
[*]Mac OS X isn't a true UNIX, it doesn't even use X Windows for its graphics but instead a proprietary Apple graphics server which uses post script data.

[*]Pretty much every OSX app uses Cocoa as its GUI toolkit, which is Apple's own proprietary GUI toolkit. Cocoa doesn't exist for other platforms than OSX.

[*]Actually, pretty much every Mac app is using purely proprietary apple APIs for everything from sound, to images, to databases.
[/LIST]

It's just not gonna happen. The fact that it uses Intel processors doesn't mean a thing, Linux ran on every processor imaginable before Apple went to Intel.

---

### Post by ssam on 2006-05-23
it would take someone writing the equivilent of wine, but for all the mac os x APIs.

i imagine it would be a slightly easier task. linux and mac os x have more similarities than linux and windows. the mac os x kernel is opensource. you heard lots of complaints about the windows APIs being poorly documented, but i have not heard similar about mac os x's. mac os x does not have the same amount of backwards comapatablity windows has. bits of gnustep might be useable.

it would still be a huge task, and i have not heard of anyone starting it.

---

### Post by Engnome on 2006-05-23
[QUOTE=ssam]
...the mac os x kernel is opensource. you heard lots of complaints about the windows APIs being poorly documented, but i have not heard similar about mac os x's. mac os x does not have the same amount of backwards comapatablity windows has. bits of gnustep might be useable.
[/QUOTE]
The mac OS X kernel for intel is not open source. [http://www.madpenguin.org/cms/?m=show&id=6888](http://www.madpenguin.org/cms/?m=show&id=6888)

---

