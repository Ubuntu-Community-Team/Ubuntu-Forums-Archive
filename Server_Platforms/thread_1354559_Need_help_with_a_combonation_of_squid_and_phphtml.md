---
title: "Need help with a combonation of squid and php/html"
date: 2009-12-14
forum: Server Platforms
---

### Post by pehden on 2009-12-14
[URL="https://pehden.ath.cx/forum/viewtopic.php?p=14&sid=5b0a7ce0e5226192dfb82a89093689df#p14"]
[/URL]
  			  			Ok Im trying to set up a proxy page on my server that when you go to the page it ask you to enter an url when you enter it then press go a frame below would show the page you wanted but it would be proxied from my site instead of actually loading as you. Every time I post the url to the proxy page i get these errors.

Example without posting to the proxy.
[Code_]_[]("https://pehden.ath.cx/forum/viewtopic.php?f=5&t=10&p=14&sid=5b0a7ce0e5226192dfb82a89093689df#")Invalid Request error was encountered while trying to process the request:

    GET / HTTP/1.1
    Host: ***************
    User-Agent: Mozilla/5.0
    Accept-Language: en-us,en;q=0.5
    Accept-Encoding: gzip,deflate
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Connection: keep-alive
    Referer: [http://******](http://******)
[/code]


This is with posted url as [www.example.com]("http://www.example.com/")
[Code][URL="https://pehden.ath.cx/forum/viewtopic.php?f=5&t=10&p=14&sid=5b0a7ce0e5226192dfb82a89093689df#"]
[/URL]ERROR
The requested URL could not be retrieved

Invalid Request error was encountered while trying to process the request:

    GET /www.example.com HTTP/1.1
    Host: ****
    User-Agent: Mozilla/5.0 
    Accept-Language: en-us,en;q=0.5
    Accept-Encoding: gzip,deflate
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
    Keep-Alive: 300
    Connection: keep-alive
    Referer: *****
    Cookie: 


Some possible problems are:

    *

      Missing or unknown request method.
    *

      Missing URL.
    *

      Missing HTTP Identifier (HTTP/1.0).
    *

      Request is too large.
    *

      Content-Length missing for POST or PUT requests.
    *

      Illegal character in hostname; underscores are not allowed.

---

### Post by BkkBonanza on 2009-12-14
I don't think anyone can help without knowing more about how you are doing this. Your config and the scripts you're using for the web page.

But besides that what is your final goal with this? There is a much easier way if you simply want to proxy for your own use not as an open web site for others.

---

### Post by pehden on 2009-12-15
> **BkkBonaza said:**
> I don't think anyone can help without knowing more about how you are doing this. Your config and the scripts you're using for the web page.

But besides that what is your final goal with this? There is a much easier way if you simply want to proxy for your own use not as an open web site for others.



  Well the main purpose was to proxy for personal use while I was at another location, like lets say at work or something, and wanted to strip stuff while surfing allot faster. I was using 

```

echo "<hr />Connect.<hr />"; 
$prox = $_POST["proxy"];
$form = ' 
    <form action="#'.$prox.'" method="post"> 
    <input type="text" name="proxy"><input type="submit" value="Go!">
     
<iframe frameborder="0" src="http://pehden.ath.cx:8600/'.$prox.'" width="100%" height="400"> 
  <em><a href="http://pehden.ath.cx:8600/'.$prox.'"></a></em> 
<p>Your browser does not support iframes. We recomend <a href="http://en-us.www.mozilla.com/en-US/firefox">Firefox"</a></p> 
</iframe>
</form> 
';echo $form;

```

Did you want the squid config info?
Oh and the other part is I currently have my own site, so this was part of an issue, i did see how to forward all stuff or something as proxy but I would like more of a fetch thing instead.  So My server could go to the web pages and send me the information i wanted from them.;)

---

### Post by BkkBonanza on 2009-12-15
I thought maybe you were using this for personal use only.
There is a much easier way to do this not involving squid or any web pages.
I assume on your server you have "ssh" available for remote access?
If yes, then a single command on your home/client machine will give you a full SOCKS5 proxy that works great for this and is more flexible and secure too.

Open a terminal and type,

ssh -f user@domain -D 8080 -N

replace user@domain with your login name and server domain eg. [email]joe@mysite.com[/email]
This single command will create a socks proxy via an encrypted secure tunnel to your server. -f means run in background, and -N means don't run a shell on the server.

Now change your Firefox (or whatever browser) to use a SOCKS5 proxy at localhost:8080

Done. Now any browsing you do goes out through the tunnel and onto the web via your server. Any web site you visit will only have the IP from your web server in it's logs.

This same command will work for email, torrents, or any other type of traffic as long as you tell your program to use a SOCKS5 proxy at localhost:8080 instead of the normal destination.

To close the tunnel just kill the ssh process.

There is also a program in Synaptics called gSTM that has a gui interface to this functionality in ssh. You can add multiple tunnels and choose one from a list and just click to open/close it.

A more advanced version of this command is to use a sleep interval to autoclose it when not active for 60 seconds (or whatever delay you choose).

ssh -f user@domain -D 8080 sleep 60

ssh is incredibly powerfull and installed by default.
Hope this helps you out.

---

### Post by pehden on 2009-12-15
is there a way to do this through the web page though, so i dont have to use ssh, cause one purpose was for when im at work i wouldnt be able to use my laptop on there network, but they have there own internet cafe, just no wifi. So a way through the web browser would be something i would need to.

Although I will use that ssh when im at the hospital or any where else.

---

### Post by BkkBonanza on 2009-12-15
There are some ready made proxy scripts in php. I made one myself before but it wasn't very flexible. I have often seen these scripts but not used them. They don't need squid or anything as they do the proxying in the script.

I did a quick google on "php proxy script" and came up with this one that looks quite decent. It doesn't appear to need other software like squid (according to the requirements it needs curl but that is default in php nowadays).

[http://www.phpmyproxy.com/](http://www.phpmyproxy.com/)

Their site is also an example of it for testing.
Of course to do this you don't have to run your own as there are many free ones around the web already you could use.

It also just occurred to me that if you have squid running on your server then you can also just enter that into the proxy settings in your browser and your browser will talk to your squid directly and work fine. This would only not work if your internet cafe blocks getting to the settings in the browser though. And you'd want to be sure to change it back after so others don't use your proxy. There is also a Firefox add-on that allows quick switching of proxy with just one click.

---

### Post by pehden on 2009-12-15
The work computers wont let us change the browser settings, and all the proxy sites are blocked by key word, plus this is more of a personal use, like when i go to something i would like to be able to make it load faster as in striping what i dont want with the proxie.

Also if there is a simple configuration for the squid.conf file that would explain each thing better point me to it lol.

---

### Post by pehden on 2009-12-17
OK, I guess that guy got sick of me lol, ok. does any one know a way to configure a php page to use squid as if it was a browser?

---

### Post by pehden on 2009-12-26
> **BkkBonaza said:**
> There are some ready made proxy scripts in php. I made one myself before but it wasn't very flexible. I have often seen these scripts but not used them. They don't need squid or anything as they do the proxying in the script.

I did a quick google on "php proxy script" and came up with this one that looks quite decent. It doesn't appear to need other software like squid (according to the requirements it needs curl but that is default in php nowadays).

[http://www.phpmyproxy.com/](http://www.phpmyproxy.com/)

Their site is also an example of it for testing.
Of course to do this you don't have to run your own as there are many free ones around the web already you could use.

It also just occurred to me that if you have squid running on your server then you can also just enter that into the proxy settings in your browser and your browser will talk to your squid directly and work fine. This would only not work if your internet cafe blocks getting to the settings in the browser though. And you'd want to be sure to change it back after so others don't use your proxy. There is also a Firefox add-on that allows quick switching of proxy with just one click.


That web site doesnt have a download to the source any more.

---

### Post by pehden on 2010-05-24
> **pehden said:**
> That web site doesnt have a download to the source any more.

Its cool now though, cause Glype is way better, and set up is quick, i got the squid thing working via webmin.

---

