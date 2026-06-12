---
title: "Python scripts not working as expected w/ Apache2"
date: 2010-04-10
forum: Server Platforms
---

### Post by dodongo on 2010-04-10
So... I've been fiddling with this off and on for some months now, and figure it may be time to seek some help  :)

So I'm running Apache2, have been for some time.  Web server works, in general, as I host some static HTML content and also a mythweb instance on this machine.  All that works fine.

I've installed mod_python in the hopes of getting some Python scripts up and running, but alas, it's not been to successful.

Symptoms are this:

--I can have a script build a valid HTML document as a string and return that value from index() and the content renders as expected.  Eg:

```
def index():
    return "<html>Hello world!</html>

```

And I get "Hello world!" in my browser.

However if I run

```
def index():
    print "<html>Hello world!</html>"

```

I get an offer by the browser to download the output to disk.  Not awesome.

Thinking this might be resolved by the lack of the "Content-type:" declaration, I can run this:

```
def index():
    print "Content-type: text/html\n\n<html>Hello world!</html>"

```

And the same thing happens, an offer to download the output.

Finally, since returning the string rather than printing it seems to produce a different behavior, I tried:

```
def index():
    return "Content-type: text/html\n\n<html>Hello world!</html>"

```

And I get this in my browser:

> Content-type: text/plain

Hello World!

So uh, ehm.  I'm good and stuck.  Any thoughts?

---

