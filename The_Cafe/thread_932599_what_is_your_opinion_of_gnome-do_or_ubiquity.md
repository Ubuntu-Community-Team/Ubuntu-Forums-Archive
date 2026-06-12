---
title: "what is your opinion of gnome-do or ubiquity?"
date: 2008-09-28
forum: The Cafe
---

### Post by adamogardner on 2008-09-28
I am just discovering them, and would like to know your experiences, and preferences.  Thanks.

---

### Post by jimi_hendrix on 2008-09-28
havnt used gnome-do but i love ubiquity

---

### Post by chris4585 on 2008-09-28
I don't like gnome-do and I dont exactly see what ubiquity and gnome-do have in common..

---

### Post by adamogardner on 2008-09-28
> **chris4585 said:**
> I don't like gnome-do and I dont exactly see what ubiquity and gnome-do have in common..

well i think the difference is that ubiquity doesn't reach into your computer to view say, your pictures or whatever.  It is purely internet, where gnome-do can do both.

there commonality is that they are both text input

---

### Post by chris4585 on 2008-09-28
> **adamogardner said:**
> well i think the difference is that ubiquity doesn't reach into your computer to view say, your pictures or whatever.  It is purely internet, where gnome-do can do both.

there commonality is that they are both text input

I thought he was talking about ubiquity the installer for Ubuntu..

[https://wiki.ubuntu.com/Ubiquity]("https://wiki.ubuntu.com/Ubiquity")

---

### Post by OutOfReach on 2008-09-28
Yeah, isn't Ubiquity the Ubuntu installer?

---

### Post by zmjjmz on 2008-09-28
Ubiquity is also an awesome FF plugin.
Anywars, I don't really use either, although supposedly they're totally fscking awesome.

---

### Post by cardinals_fan on 2008-09-28
Ubiquity == Win
GNOME-Do == Fail

---

### Post by adamogardner on 2008-09-28
> **chris4585 said:**
> I thought he was talking about ubiquity the installer for Ubuntu..

[https://wiki.ubuntu.com/Ubiquity]("https://wiki.ubuntu.com/Ubiquity")

Are you talking to me?  Is there a way to put this in ubiquity without having it downloaded by a third party?

CmdUtils.CreateCommand({
  name: "comments",
  author: {name: "Brian Kierstead", email: "briankierstead@gmail.com"},
  description: "Reveal comments in the code.",
  execute:function() {
    doc = context.focusedWindow.document
    if(!doc)
      return;
 
    ss = addStyleSheet(doc);
    if(ss)
     addStyles(ss);
 
    bodyNodes = doc.body.childNodes;
    for(var i=0; i < bodyNodes.length; i++){
      if(bodyNodes[i].nodeType==8){
        var div = context.focusedWindow.document.createElement( "div" );
        div.innerHTML = '<a class="info" href="#" onclick="javascript:return false;">'
          + '<image src="http://en.wikipedia.org/skins-1.5/monobook/external.png" border="0" />'
          + '<span>' + bodyNodes[i].nodeValue + '</span></a>';
        try{
          bodyNodes[i].parentNode.removeChild(bodyNodes[i]);
          bodyNodes[i].parentNode.insertBefore(div, bodyNodes[i]);
        }
        catch(err){
          // this will break if node insertion is not allowed the parent
          // but what to do?
        }
      }
    }
  }
});
 
function addStyleSheet(doc){
 
  // add one if there are none
  if(!doc.styleSheets[0]){
   ss = doc.createElement("style");
   ss.type="text/css";
   ss.media="all";
   doc.getElementsByTagName("head")[0].appendChild(ss);
  }
  return doc.styleSheets[0];
}
 
function addStyles(ss)
{
  // add the rules
  ss.insertRule('a.info{'
   + 'position:relative;'
   + 'z-index:24;'
   + 'color:#000;'
   + 'font-weight: normal;}',0);
  ss.insertRule('*+html a.info{'
   + 'padding-right: 3px;}', 0);
  ss.insertRule('a.info:hover{z-index:25;}',0);
  ss.insertRule('a.info span{display: none}',0);
  ss.insertRule('a.info:hover span{'
    + 'display: block;'
    + 'font-size: 11px;'
    + 'position: absolute;'
    + 'font-weight: normal;'
    + 'top:2em;'
    + 'right:-1em;'
    + 'width: 23em;'
    + 'padding: 5px;'
    + 'max-width: 23em;'
    + 'word-wrap: break-word;'
    + 'border:1px solid #d5d7ca;'
    + 'background-color:#FCFCFA;'
    + 'color:#326175;'
    + 'text-align: left;'
    + 'z-index:25;'
    + 'white-space: pre-wrap;}', 0);
}

---

### Post by chris4585 on 2008-09-28
> **adamogardner said:**
> Are you talking to me? 

Yes I was saying I thought you were talking about Ubiquity the install for Ubuntu, I have no idea about any other ubiquity..

---

### Post by speedwell68 on 2008-09-28
Personally I think GNOME DO is great, I love it, I never have to lift my hands from the keyboard.

---

### Post by gjoellee on 2008-09-28
it saved me from reeinstalling the whole OS once.

(Gnome Panles and other did not load and hotkeys didn't work, but Gnome Do was there so I cold open the terminal and start gnome-panels)

---

### Post by cookieofdoom on 2008-09-28
I really like Gnome-Do, and I think Ubiquity (the Mozilla version) will be really useful. Hopefully there will be a way to integrate the two of them... having quicksilver type apps could get kinda confusing.

---

### Post by brunovecchi on 2008-09-28
Gnome do has changed the way I use my computer, it's THAT awesome.

---

### Post by inigomontoya on 2008-09-28
> **brunovecchi said:**
> Gnome do has changed the way I use my computer, it's THAT awesome.

I feel the same.  I hardly use the menus anymore.

---

### Post by Stefanie on 2008-09-29
i can't live without gnome-do :-) seriously, it's so cool. @cardinals & others: why don't you like it, and what do you use instead?


i use these plugins:

- gmail contacts. i set up gmail as my default e-mail client in ubuntu and this makes it even more useful
- apturl: install packages
- files and folders: indexes your folders so you can browse and open your files with gnome-do
- gnome session management: log out, shutdown, reboot etc 
- gnome terminal
- google calculator
- locate to locate files
- search google, returns results to gnome-do

---

### Post by SupaSonic on 2008-09-29
I didn't like gnome do. Maybe if I gave it more time it'd grow on me, but after using it for 5 minutes I removed it.

---

### Post by Canis familiaris on 2008-09-29
> **cardinals_fan said:**
> Ubiquity == Win
GNOME-Do == Fail

FAIL.
That is only *your* opinion. ;)

Seriously calling something FAIL just because it doesn't suit you is not a good idea. ;)

I use Opera. Should I call Ubiquity as FAIL? No I shouldn't.

---

### Post by adamogardner on 2008-09-29
> **Anurag_panda said:**
> FAIL.
That is only *your* opinion. ;)

Seriously calling something FAIL just because it doesn't suit you is not a good idea. ;)

I use Opera. Should I call Ubiquity as FAIL? No I shouldn't.

I don't believe he was claiming to be stating a fact, when you made your first point. I asked for opinions and thats what everyone (not just he) is offering. 
Then you followed up with an illogical supporting statement about his choice of word.  'Fail' is a bit harsh but perhaps that is his opinion of it, and I value it.    
And frankly, You shouldn't mark Ubiquity as fail because you haven't the experience to formulate a substantial opinion of it since, as you claim, you use opera.  I don't see the relevancy from one line to the next.
I presume that you use gnome-do?

---

### Post by Canis familiaris on 2008-09-30
> **adamogardner said:**
> I don't believe he was claiming to be stating a fact, when you made your first point. I asked for opinions and thats what everyone (not just he) is offering. 
Then you followed up with an illogical supporting statement about his choice of word.  'Fail' is a bit harsh but perhaps that is his opinion of it, and I value it.    
And frankly, You shouldn't mark Ubiquity as fail because you haven't the experience to formulate a substantial opinion of it since, as you claim, you use opera.  I don't see the relevancy from one line to the next.
I presume that you use gnome-do?

*sigh*
I dont know whether my statement was illogical or amounted to trolling. If it came that way I apologise, since I had no intention.But I think you misunderstood what I meant to say.
 I only wanted to say calling something as "FAIL" without facts or figures and only as an expression of personal opinion is not nice.
Then in a sarcastic way I said whether should I call Ubiquity as FAIL when I don't even use it. I did not express any opinion about Ubiquity there.
In case you show an opinion, negative ones in particular - You should back it up rather than making a silly vague statement.

Anyway, Yes I use GnomeDo, and I find wonderful to be able to launch programs and do so many other things without using the mouse.

---

### Post by nothingspecial on 2008-09-30
Gnome-do is awesome. It even has a plugin for squeezecenter (wireless streaming software). I sit at my pc at one end of the room, type the first few letters of a song (or artist,album,etc), hit enter and it`s playing on my music system on the other side of the room.  Soo much better than crappy pc speakers.
 How cool is that?

---

### Post by adamogardner on 2008-09-30
> **nothingspecial said:**
> Gnome-do is awesome. It even has a plugin for squeezecenter (wireless streaming software). I sit at my pc at one end of the room, type the first few letters of a song (or artist,album,etc), hit enter and it`s playing on my music system on the other side of the room.  Soo much better than crappy pc speakers.
 How cool is that?

thats way cool.  You probably need some special kind of sound system?  One that picks up wireless, what do you use?  I guess I have pc speakers that plug in.

---

### Post by nothingspecial on 2008-09-30
> **adamogardner said:**
> thats way cool.  You probably need some special kind of sound system?  One that picks up wireless, what do you use?  I guess I have pc speakers that plug in.

I have 3 squeezeboxes -

[http://www.slimdevices.com/pi_squeezebox.html](http://www.slimdevices.com/pi_squeezebox.html)

They run with this free open source  software

[http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)

I have one in the living room one in the kitchen and one in the bedroom. You hook em up to your music systems and you can play all the music on your pc, listen to internet radio live365, Shoutcast etc. They have a lastfm plugin and a bbc iplayer plugin so you can listen to any bbc radio proramme from the last 7 days.
They can play stuff independantly or you can sync them so they all play the same thing. Music piping round your house (great for parties).
You do this with a remote control that works a bit like how phones do that predictive text thing. So click search, press grateful and up come the Dead. I remember your Jerry avatar.

They`re the best thing I`ve ever bought. Probably the finest invention since the wheel.

And no I don`t work for them I just love these things.

---

