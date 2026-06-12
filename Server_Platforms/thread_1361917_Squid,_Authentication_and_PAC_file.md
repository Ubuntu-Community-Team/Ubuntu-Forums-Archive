---
title: "Squid, Authentication and PAC file"
date: 2009-12-22
forum: Server Platforms
---

### Post by yug23 on 2009-12-22
I am trying to do something which does not seem to be very common- any help most appreciated!

 I have set up a squid proxy on my VPS with NCSA user authentication. This means that if the proxy is set in the Firefox configuration, when a user opens the browser it will ask for a username and password. This is all working well.

The problem is that I don't want the users to go via the proxy on every website. So I made a proxy.pac file to use the proxy on only certain sites. I have used the Google pac file tester and it seems to be fine, but it seems that the web browser is always connecting directly to the internet and never using the proxy.

Here is the pac file:

```

function FindProxyForURL(url, host)
{

	url = url.toLowerCase();
	host = host.toLowerCase();

	var proxy_no = "DIRECT";
        var MyProxy = "myserver:3128";
        var MySites =
        [
        "site1.com",
        "site2.co.uk"
    ];
    
    for (var i in MySites)
    {
        if (  shExpMatch(host, '*'+MySites[i])  )
        {
            return MyProxy;
        }
    }   

	return proxy_no;

}

```

I modified it so that it would use a local SSH tunnel instead of my squid proxy just to test it, and this worked, so I suspect that it might be the authentication which is stopping the pac file from working.

Any thoughts, please let me know, my brain hurts!

---

### Post by yug23 on 2009-12-23
Bump! 

I could really do with some help on this one guys... please?

If there is any way of using any kind of authenticated proxy with pac or wpad files I am willing to be flexible, it doesn't need to be Squid if something else works better...

Thanks.

---

### Post by yug23 on 2009-12-23
It turned out that the authentication was not the problem, simply that I needed to put the word PROXY and a space before the actual proxy address- so:

function FindProxyForURL(url, host)
{

	url = url.toLowerCase();
	host = host.toLowerCase();

	var proxy_no = "DIRECT";
        var MyProxy = "PROXY myserver:3128";
        var MySites =
        [
        "site1.com",
        "site2.co.uk"
    ];
    
    for (var i in MySites)
    {
        if (  shExpMatch(host, '*'+MySites[i])  )
        {
            return MyProxy;
        }
    }   

	return proxy_no;

}

Hope that helps someone :)

---

### Post by koenn on 2009-12-23
i was just about to dig up my notes on pac and wpad when I noticed you already solved the issue yourself.
Good for you.

---

