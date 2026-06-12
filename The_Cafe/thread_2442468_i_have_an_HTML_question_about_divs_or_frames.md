---
title: "i have an HTML question about divs or frames"
date: 2020-05-04
forum: The Cafe
---

### Post by Skaperen on 2020-05-04
i am posting this in the cafe because it is not about Ubuntu.  it is about HTML and i don't want to go creating another account somewhere to find an answer.

i have seen a few web sites that are able to create what look like frames, which i hear are going away.  i don't know if they are still using the old frames.  but the can make a big area that is larger than the screen, and do scrolling to move around the big area, up/down and left/right.  some even have dragging so you can just drag the big area in any direction to change the view.

what i want to do is create a big area of some specific dimensions larger the screen that can be scrolled in the screen view and open a web site in that area.  the intent is to view that site as if i had a larger screen but just view a portion at a time.  i can do this in my video driver already but it's a big hassle because i need to completely log out and log in to the new screen size.  it disrupts what i am doing.  i'd rather have the web browser do it, which it obviously can do.

does anyone know the HTML to set this up?  i'll then make some Python code to generate the HTML dynamically.

---

### Post by Dennis N on 2020-05-04
I've made them like you see here:
[https://www.w3schools.com/html/html_iframe.asp](https://www.w3schools.com/html/html_iframe.asp)
with two frames - the left frame is an index to other web pages, which open inside the right frame. Both frames are scrolable if a dimension isn't set as a specific number of pixels. Click on "HTML iframes" to read the topic on constructing them. (When I did them, they tag was just <FRAME> not <IFRAME> but the former still works in Firefox).

---

### Post by sdsurfer on 2020-05-04
Nearly everything you mention can be achieved with CSS and allowing the browser to do what it does. Frames and iframes are problematic for various reasons I won't get into. You can approach it many ways.

Dragging is done with jQuery, most often with the jQuery UI plugin (or some framework that incorporates it.)

When you say "bigger than the screen" are you doing any viewport detection, or have a specific target in mind? The latter would be probably easiest. Off the top of my head, if I have a target content area of 5000 pixels, you could have a wrapper container (body: width 100%) and  a div (width: 5000px) inside it. This will allow the browser's natural scrollbars to access the content. You can further control container scrolling with with overflow: scroll which controls both X and Y. You can control each individually with overflow-x and overflow-y. The example below doesn't implement dragging, but it's a starting point. I put a small one inside it so you can see how it works.

```
<!DOCTYPE [COLOR=#0000ff]**html**[/COLOR]>
<[COLOR=#000080]**html **[/COLOR][COLOR=#0000ff]**lang**[/COLOR][COLOR=#008000]**="en"**[/COLOR]>
<[COLOR=#000080]**head**[/COLOR]>
  <[COLOR=#000080]**meta **[/COLOR][COLOR=#0000ff]**charset**[/COLOR][COLOR=#008000]**="UTF-8"**[/COLOR]>
  <[COLOR=#000080]**title**[/COLOR]>Overflow example</[COLOR=#000080]**title**[/COLOR]>
  <[COLOR=#000080]**style **[/COLOR][COLOR=#0000ff]**type**[/COLOR][COLOR=#008000]**="text/css"**[/COLOR]>
    [COLOR=#000080]**body **[/COLOR]{
      [COLOR=#0000ff]**width**[/COLOR]: [COLOR=#0000ff]90[/COLOR]%;
      [COLOR=#0000ff]**margin**[/COLOR]: [COLOR=#0000ff]1[/COLOR][COLOR=#008000]**em auto**[/COLOR];
    }
    [COLOR=#000080]**#scroll-me **[/COLOR]{
      [COLOR=#106f03]/* not needed in this scenario
[/COLOR][COLOR=#106f03]      overflow-x: scroll;
[/COLOR][COLOR=#106f03]      overflow-y: visible;
[/COLOR][COLOR=#106f03]       */
     [/COLOR][COLOR=#0000ff]**background**[/COLOR]: [COLOR=#000080]**#f7f7f7**[/COLOR];
      [COLOR=#0000ff]**width**[/COLOR]: [COLOR=#0000ff]5000[/COLOR][COLOR=#008000]**px**[/COLOR];
      [COLOR=#106f03]/* This is the initial height - content forces it vertically */
      [/COLOR][COLOR=#0000ff]**height**[/COLOR]: [COLOR=#0000ff]90[/COLOR]%;
      [COLOR=#0000ff]**top**[/COLOR]: [COLOR=#0000ff]1[/COLOR][COLOR=#008000]**em**[/COLOR];
      [COLOR=#0000ff]**left**[/COLOR]: [COLOR=#0000ff]1[/COLOR][COLOR=#008000]**em**[/COLOR];
      [COLOR=#0000ff]**border**[/COLOR]: [COLOR=#0000ff]1[/COLOR][COLOR=#008000]**px solid **[/COLOR][COLOR=#000080]**#000**[/COLOR];
    }
    [COLOR=#000080]**#scroll-me-too **[/COLOR]{
      [COLOR=#0000ff]**width**[/COLOR]: [COLOR=#0000ff]200[/COLOR][COLOR=#008000]**px**[/COLOR];
      [COLOR=#0000ff]**height**[/COLOR]: [COLOR=#0000ff]100[/COLOR][COLOR=#008000]**px**[/COLOR];
      [COLOR=#0000ff]**float**[/COLOR]: [COLOR=#008000]**left**[/COLOR];
      [COLOR=#0000ff]**margin**[/COLOR]: [COLOR=#0000ff].5[/COLOR][COLOR=#008000]**em**[/COLOR];
      [COLOR=#106f03]/* nowrap added only to force the scroll */
      [/COLOR][COLOR=#0000ff]**white-space**[/COLOR]: [COLOR=#008000]**nowrap**[/COLOR];
      [COLOR=#0000ff]**overflow-x**[/COLOR]: [COLOR=#008000]**scroll**[/COLOR];
      [COLOR=#0000ff]**overflow-y**[/COLOR]: [COLOR=#008000]**visible**[/COLOR];
      [COLOR=#0000ff]**background**[/COLOR]: [COLOR=#000080]**#fff**[/COLOR];
      [COLOR=#0000ff]**border**[/COLOR]: [COLOR=#0000ff]1[/COLOR][COLOR=#008000]**px solid **[/COLOR][COLOR=#000080]**#ff0000**[/COLOR];
    }
  </[COLOR=#000080]**style**[/COLOR]>
</[COLOR=#000080]**head**[/COLOR]>
<[COLOR=#000080]**body**[/COLOR]>

<[COLOR=#000080]**div **[/COLOR][COLOR=#0000ff]**id**[/COLOR][COLOR=#008000]**="scroll-me"**[/COLOR]>
  <[COLOR=#000080]**p **[/COLOR][COLOR=#0000ff]**id**[/COLOR][COLOR=#008000]**="scroll-me-too"**[/COLOR]>
    I am a very small element controlled with overflow-x.</[COLOR=#000080]**p**[/COLOR]>
  </[COLOR=#000080]**p**[/COLOR]>
  <[COLOR=#000080]**p**[/COLOR]>This is a container scrolling right beyond the viewport.</[COLOR=#000080]**p**[/COLOR]>
  <[COLOR=#000080]**p**[/COLOR]>Do a huge Lorem Ipsum dump below this line, say, 50 paragraphs, to see the effect. The browser's scroll mechanisms will handle the scrolling.</[COLOR=#000080]**p**[/COLOR]>
</[COLOR=#000080]**div**[/COLOR]>

</[COLOR=#000080]**body**[/COLOR]>
</[COLOR=#000080]**html**[/COLOR]>

```

Lorem Ipsum generator: [https://www.lipsum.com/](https://www.lipsum.com/)

---

### Post by sdsurfer on 2020-05-04
Hmm, in retrospect you may want to add position: absolute or position: fixed to scroll-me, it is forcing the body larger than 90% (you can't see it, but it is.)

---

### Post by Skaperen on 2020-05-04
i am not yet understanding what you guys are talking about.  my knowledge of this is creating a [looped panorama page]("http://ipal.net/vance/") over 10 years ago and having used a couple web based email client where it had a "window" showing the current email which was often wider than the "window" i viewed it in, using the scroll keys to select what part of the current email display i wanted to see.

i suggest the following test.  create the necessary HTML, CSS (embedded in that HTML), Javascript (embedded in that HTML) that opens a youtube.com video at 3840x2160 (4K) and works on whatever screen size that accesses it, allowing whoever accesses it to see a 4K video at full resolution, in part (such as HD) and scroll around in it.

even better, accept the video URL or code number in your URL.

---

### Post by Skaperen on 2020-05-04
maybe i can run an xvnc X server at 3840x2160 and access it with a VNC client (such as remmina) and that VNC client will create the necessary scrolling.  the last time i tried this it failed because the display environment code started by X wanted to start X.

---

