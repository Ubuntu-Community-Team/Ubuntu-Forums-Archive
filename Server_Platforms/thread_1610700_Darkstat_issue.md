---
title: "Darkstat issue"
date: 2010-11-01
forum: Server Platforms
---

### Post by collimic on 2010-11-01
I am running darkstat on my ubuntu 8.10 server.
It use to work but I did an apt-get update ; apt-get upgrade one day and now when I goto mydomain.ltd:666 I get a plain white page.
If I view the source I can see that it is tring to load but nuthing is loading to the site.
Here is a copy of that I get when I do a view-source:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> 
<html xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
 <link rel="stylesheet" href="/style.css" type="text/css"/> 
<title>darkstat 3.0.708 : graphs (eth0)</title> 
<script src="graph.js" type="text/javascript"></script> 
</head> 
<body> 
<div class="menu"> 
<ul class="menu"> 
<li class="label">darkstat 3.0.708</li><li><a href="/">graphs</a></li><li><a href="/hosts/">hosts</a></li><li><a href="http://dmr.ath.cx/net/darkstat/">homepage</a></li></ul> 
</div> 
<div class="content"> 
<h2 class="pageheader">Graphs (eth0)</h2> 
<p> 
<b>Running for</b> <span id="rf">5 hrs, 44 mins, 49 secs</span><b>, since</b> 2010-11-01 00:13:55 UTC+0000<b>.</b><br/> 
<b>Total</b> <span id="tb">2,016,195,228</span> <b>bytes in</b> <span id="tp">3,498,763</span> <b>packets.</b><br/> 
</p> 
<div> 
<div class="outergraph" id="g0">Graphs require JavaScript.</div> 
<div class="outergraph" id="g1"></div> 
<div style="clear:both"></div> 
<div class="outergraph" id="g2"></div> 
<div class="outergraph" id="g3"></div> 
<div style="clear:both"></div> 
<div id="graph_buttons"></div> 
</div> 
<script type="text/javascript"> 
//<![CDATA[
var graph_width = 320;
var graph_height = 200;
var bar_gap = 1;
 
var graphs_uri = "/graphs.xml";
var graphs = [
 {id:"g0", name:"seconds", title:"last 60 seconds", bar_secs:1},
 {id:"g1", name:"minutes", title:"last 60 minutes", bar_secs:60},
 {id:"g2", name:"hours", title:"last 24 hours", bar_secs:3600},
 {id:"g3", name:"days", title:"last 31 days", bar_secs:86400}
];
 
window.onload = graph_loader;
//]]>
</script> 
</div> 
</body> 
</html>
```

Any help would be great.
Thank you.

---

### Post by lombaardcj on 2010-11-08
Hi,

Have you tried asking over at the forum for darkstat.  Their might have been minor change in the way things are set up, and you just happen to hit one of those snags.

This has happened to me a few times in the past where a "safe" update, was not really so safe, and only to find out you've got problems.

I'm looking at Darkstat for my own use, and will let you know if I make any progress.

---

