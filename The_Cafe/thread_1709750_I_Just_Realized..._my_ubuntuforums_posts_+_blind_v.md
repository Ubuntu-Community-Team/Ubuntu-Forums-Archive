---
title: "I Just Realized... my ubuntuforums posts + blind viewer = fail"
date: 2011-03-18
forum: The Cafe
---

### Post by earthpigg on 2011-03-18
So, I asked an acquaintance of mine to check out my blog and verify that it was accessible to her using the screen reading software that she relies upon to access the web.

I was pretty happy to hear that it was, and she complimented me on my descriptive alt= text associated with maps.

As an aside for anyone maintaining a website of any form, the process is fairly simple:

1) go to the edit raw html or edit html mode in whatever interface you are using.
2) look for any instance of 
```
<img src="http://whatever.jpg" width=whatever>
``` 
and change it to 
```
<img src="http://whatever.jpg width=whatever alt="Description of picture, preferably detailed, goes here.">
```
3) for the most part, the screen reading software should take care of the rest.

There are [detailed directions]("http://www.w3.org/") available for policy makers, but the above combined with closed captions of any audio (for the Deaf) will take you most of the way. (note to self: find out if screen-reading software can locate a 'play' button in various types of embedded video. videos usually have pictures *and sound*, after all.)

Anyways, back to ubuntuforums.org posts: I realized that of my 2300+ posts, there are likely hundreds that are not accessible to screen-reading software because I attached pictures  (screen-shots, etc) without any text description. And, I decided that that is a bad thing, and I need to fix that in future posts because there is no telling who will or may come across them via google in the future.

So, here is what I am thinking I will implement for myself in the future:
> 1) Screenshots can augment the text of the post, but the text must include an adequate description that will get the message across without requiring that the picture be viewed.
2) If I attach any pictures, the last part of the post will include a "attached is a picture of..." section.
3) If I embed any pictures, the narrative of the post will describe them in such a way that the post is still comprehensive and make sense without the pictures.
4) The above will be *especially* emphasized in future posts of a technical nature.
5) In threads that have close to zero likelihood of being of any interest to someone that can't see, no requirement for any of the above. An example of this would be the vast majority of posts in the monthly 'screenshots' thread.

Did I miss anything? Reasonable compromise with myself between laziness and accessibility?

I realize that some problems, such as GRUB being broken, would require a sighted person to fix. 

Other problems - especially problems that occur while in gnome (ex, update manager saying "E:Some index files failed to download, they have been ignored, or old ones used instead.") - really shouldn't require sight in order to repair. :P

And, if the problem *does* require a sighted person to fix, the barrier should be the software itself (something I have only slight control over via bug reports and the like), and *not* a post of mine (something I have complete control over).

Attached is a picture of a puppy that is adorable because he is wrapped in a towel with only his face sticking out with his tongue hanging off to the side.

---

