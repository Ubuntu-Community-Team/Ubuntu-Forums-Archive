---
title: "ajaxterm with proxy"
date: 2008-08-16
forum: Server Platforms
---

### Post by quattrodrifter on 2008-08-16
Hello, my name is Chris and I'm new here.

I'm running a server at home with an apache. Now i tried to install ajaxterm with https as explained in the ubuntuusers wiki as well. 

I can reach the terminal at the local machine with [http://localhost:8022](http://localhost:8022)

Then i tried a mod_proxy_html like this

```

      ProxyRequests Off
      <Proxy *>
              Order deny,allow
              Allow from all
      </Proxy>
      ProxyPass /ajaxterm/ http://localhost:8022/
      ProxyPassReverse /ajaxterm/ http://localhost:8022/


```

I can load the page with ssl and without. But thats not the problem. The page is empty, but the title is present in the Browser.
So i think i cant get the java scripts because the page source code looks like this:

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
	<title>Ajaxterm</title>
	<meta http-equiv="content-type" content="text/html; charset=UTF-8"/>
	<link rel="stylesheet" type="text/css" href="ajaxterm.css"/>
	<script type="text/javascript" src="sarissa.js"></script>
	<script type="text/javascript" src="sarissa_dhtml.js"></script>
	<script type="text/javascript" src="ajaxterm.js"></script>

	<script type="text/javascript">
	window.onload=function() {
		t=ajaxterm.Terminal("term",80,25);
	};
	</script>
</head>
<body>
<div id="term"></div>
</body>
</html>


```

my ssl logfile says:

```

Sat Aug 16 21:19:33 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:34 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:34 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:34 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:34 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:36 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:36 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:36 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:19:36 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:28:22 2008] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sat Aug 16 21:28:38 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:28:38 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:28:38 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm
[Sat Aug 16 21:28:38 2008] [error] [client 192.168.3.101] File does not exist: /htdocs, referer: https://192.168.3.103/ajaxterm

```

Sorry for bad english.

I'm getting crazy. Any Ideas?:confused:


UPDATE:
I forgot:

Its running with Ubuntu 7.10

If you need some more files. tell me which, so i will post them.

---

### Post by cebe11 on 2008-10-05
Did you ever get this to work?  I'm having no luck at all getting ajaxterm to run, at least from the wan side, works fine on the lan side.
  Anyone have any success with this?

EDIT:  Got it going.  Was a port port forward problem with router

---

### Post by haarausfall on 2009-02-21
Hi quattrodrifter,

could you fix this? I have exactly the same problem running it on Apache as mod_proxy.

You can also write me in German, if its easier for you..

Thanks and best regards,
Markus

---

