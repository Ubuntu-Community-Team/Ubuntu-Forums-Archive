---
title: "PHP: XML Always Parsed as Empty - Bad Configuration?"
date: 2009-06-08
forum: Server Platforms
---

### Post by Jesdisciple on 2009-06-08
I recall that PHP once parsed XML just fine, and I'm not sure when that changed.  I'm using this slight modification of the test found [on the PHP site]("http://us3.php.net/manual/en/domdocument.loadxml.php"):```
$doc = new DOMDocument();
$doc->loadXML('<root><node/></root>');
var_dump($doc);
```Inside a function, this gives:```
object(DOMDocument)#1 (0) {
}
```or by itself:```
NULL
```The only thing I recall which might have changed anything is installing PEAR and PHPUnit.

Help, please?

---

### Post by LepeKaname on 2009-06-08
> I recall that PHP once parsed XML just fine

Sorry, but what does "parsed" means exactly?

For me: var_dump($doc);
Returned: object(DOMDocument)[1]
And echo $doc->saveXML();
Returned: [HTML]<?xml version="1.0"?>
<root><node/></root>[/HTML]

As expected... so, maybe I don't understand what is the problem?

---

### Post by Jesdisciple on 2009-06-09
The same operation incorrectly fails on my computer, so I'm wondering what would cause that.  The fact that it's different in/out of functions suggests that it's not just a DOMDocument problem.

EDIT: The stuff about errors that was here was my fault, not PHP's.

I tried using SimpleXML which works, but it's inadequate for at least one thing I was doing with DOM.  I was importing and appending a node (the document element of another document), and SimpleXML can't do either.

Thanks for trying to help.  :)

---

### Post by Jesdisciple on 2009-06-09
This problem is located within my home directory.  I reinstalled Ubuntu on this partition, keeping my profile intact.  I wonder if that narrows things down enough to find it?

---

### Post by LepeKaname on 2009-06-09
In you phpinfo() what do you have in DOM and libxml?

I have this:

```

DOM/XML 	enabled
DOM/XML API Version 	20031129
libxml Version 	2.6.32
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

```

```
libXML support 	active
libXML Version 	2.6.32
libXML streams 	enabled 
```]

I think that you should reinstall php and apache removing any configuration file you must have, and test if it is fixed. Then, start adding you custom configuration one by one. How does that sound?

---

### Post by Jesdisciple on 2009-06-09
My phpinfo is identical on those points.

I uninstalled and reinstalled (except /etc/apache) before the overhaul.  Then I tried compiling PHP and debugging DOM to find why nothing was in the object, but that was some really deep water, miles over my head.  (I was unable to test the problem on the other PHP because of bad configuration.)

But anyway, the only thing I kept across Ubuntu installs was the list of installed programs, so hasn't that already been done?  Unless of course /home contains config files.

Thanks.

---

### Post by Jesdisciple on 2009-06-10
Well, this is certainly news...  I just reproduced this on my deployment server.  Weird...  As it's in a completely empty script, doesn't that mean it has to be a server problem, not a script one?

---

### Post by LepeKaname on 2009-06-10
It seems is a script problem then...

---

### Post by Jesdisciple on 2009-06-10
???  You said it ran fine on your server.  How can such a simple script contain a bug?

---

### Post by LepeKaname on 2009-06-10
So you are not running anything else? What happen if your XML actually have data? does it return something?
Something like:
```
$doc->loadXML('<root><node>Hey! here is my data!</node></root>');
```

---

### Post by Jesdisciple on 2009-06-10
How dense can I get?  saveXML works; as you seem to have guessed, I wasn't checking the HTML source for XML.  Still, I thought var_dump once worked to show the document's structure, and I really think it *should* work for all objects.

Thanks.

---

