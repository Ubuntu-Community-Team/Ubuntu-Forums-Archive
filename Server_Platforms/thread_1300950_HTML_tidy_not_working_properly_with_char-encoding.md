---
title: "HTML tidy not working properly with char-encoding"
date: 2009-10-25
forum: Server Platforms
---

### Post by wonderingwout on 2009-10-25
Hi,

I installed tidy on my Ubuntu server to run inside a Rails application under Passenger.
At first all seemed to work fine but in some cases it doesn't.

I use it with the tidy gem and the rails_tidy plugin, as found here:
[http://blog.cosinux.org/pages/rails-tidy](http://blog.cosinux.org/pages/rails-tidy)

Locally all is running perfectly (on a MacOSX).
But as soon as I deploy the application to the Ubuntu server things go wrong.

Some pages are loading and some are not.
I get an apache error and I found out that is has to do with the Rails application providing no or corrupt data.

As I started playing with the settings I noticed the char-encoding setting caused the corrupt data.
So I fooled around with the input/ouput-encodings but it wouldn't help.

Any ideas on what this could be?
Maybe a Passenger or Apache related issue?

---

### Post by Lars Noodén on 2009-10-26
> **wonderingwout said:**
> 
As I started playing with the settings I noticed the char-encoding setting caused the corrupt data.
So I fooled around with the input/ouput-encodings but it wouldn't help.


Please provide some more details about what you've tried and the errors it produces.

---

