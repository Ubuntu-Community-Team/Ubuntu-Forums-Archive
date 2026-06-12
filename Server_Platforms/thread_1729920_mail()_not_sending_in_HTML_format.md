---
title: "mail() not sending in HTML format"
date: 2011-04-15
forum: Server Platforms
---

### Post by rmmsteve on 2011-04-15
I'm not sure if this is a server problem or a PHP problem. I've tried the code on other servers and it seems to work - so I assume it's a server problem. I am running it on Ubuntu 10.10. 

When run this code, it does not render in HTML on my OSX mail reader:

[php]
<?php
$to = "xxx@xxx.com";
$subject = "HTML email";

$message = "
<html>
<head>
<title>HTML email</title>
</head>
<body>
<p>This email contains HTML Tags!</p>
<table>
<tr>
<th>Firstname</th>
<th>Lastname</th>
</tr>
<tr>
<td>John</td>
<td>Doe</td>
</tr>
</table>
</body>
</html>
";

// Always set content-type when sending HTML email
$headers = "MIME-Version: 1.0" . "\r\n";
$headers .= "Content-type:text/html;charset=iso-8859-1" . "\r\n";

// More headers
$headers .= 'From: <xxx@xxx.com>' . "\r\n";

mail($to,$subject,$message,$headers);
?> Mail Sent!
[/php]BODY OUTPUT:

```

Content-type:text/html;charset=iso-8859-1

From: <xxx@xxxx.com>
Message-Id: <20110415162239.466D411C0A7A@ubuntu>
Date: Fri, 15 Apr 2011 12:22:39 -0400 (EDT)


<html>
<head>
<title>HTML email</title>
</head>
<body>
<p>This email contains HTML Tags!</p>
<table>
<tr>
<th>Firstname</th>
<th>Lastname</th>
</tr>
<tr>
<td>John</td>
<td>Doe</td>
</tr>
</table>
</body>
</html>


```

---

### Post by SeijiSensei on 2011-04-15
You need a lot more than just a Content-Type header.  You need to include dividers and a couple of other things.  Usually you also want to include a plain-text version for people who don't accept HTML mail.

Your best bet is to send yourself an HTML-formatted email and the view the entire message source.  Then use that as a template for the message to be generated in PHP.

I took me an hour or two to figure out how to do this correctly.

---

