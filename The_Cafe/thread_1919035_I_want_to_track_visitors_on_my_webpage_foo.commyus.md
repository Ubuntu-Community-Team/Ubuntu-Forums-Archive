---
title: "I want to track visitors on my webpage foo.com/myusername"
date: 2012-02-02
forum: The Cafe
---

### Post by hanzj on 2012-02-02
Hello,

I have a webpage on a domain that I don't own. I prefer not to get into which domain it is. The webpage allows simple html tracking code, like what flagcounter.com offers:

```

<a href="http://s03.flagcounter.com/more/XXXX"><img src="http://s03.flagcounter.com/count/gbB5/bg_FFFFFF/txt_000000/border_CCCCCC/columns_4/maxflags_19/viewers_3/labels_1/pageviews_1/flags_1/" alt="free counters" border="0"></a>
```

but it won't accept javascript code, like Google Analytics:

```

<script type="text/javascript">

  var _gaq = _gaq || [];
  _gaq.push(['_setAccount', 'UA-2886XXXX-1']);
  _gaq.push(['_trackPageview']);

  (function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
  })();

</script>
```
When I try to save the webpage with the javascript code, the page doesn't keep the code.


I want to invisible track my visitors, so flagcounter is out of the picture.
I want to track IP address and time/date of visit. What are my options?

---

### Post by Nytram on 2012-02-02
It's been a while since I've used HTML but I think the <img> tag allows *width* and *height* as parameters so you could make the image a single pixel in size, and it would go unnoticed.

---

### Post by aeiah on 2012-02-02
> **Nytram said:**
> It's been a while since I've used HTML but I think the <img> tag allows *width* and *height* as parameters so you could make the image a single pixel in size, and it would go unnoticed.

this. or put it in a hidden div

---

### Post by CharlesA on 2012-02-02
Both of those sound quite dodgy.

If you do not own the domain name, just use what it allows, don't try to get around what they allow.

---

### Post by hanzj on 2012-02-02
OK. But what tracking sites/services can do this? I am new to this.

---

### Post by CharlesA on 2012-02-02
You posted one in the OP.

---

### Post by N00b-un-2 on 2012-02-02
sounds to me like someone is trying to track who's looking them up on facebook.

---

### Post by CharlesA on 2012-02-02
> **N00b-un-2 said:**
> sounds to me like someone is trying to track who's looking them up on facebook.
If not that, then it is sure phishy sounding.

---

### Post by hanzj on 2012-02-02
but i want one that gives vistor's:
--IP address
--time of visit
--duration of visit

---

### Post by CharlesA on 2012-02-02
That is something you can get from server logs, but it is not something you would normally have a need for.

This thread is closed.

---

