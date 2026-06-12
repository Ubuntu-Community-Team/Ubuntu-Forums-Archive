---
title: "[SOLVED] help with some html?"
date: 2008-08-11
forum: The Cafe
---

### Post by mpgarate on 2008-08-11
im putting up a basic website that just has a image which links to a myspace account. for some reason it works flawlessly in firefox, but in ie7 the link does not work.

[HTML]
<html><a href="http://www.ubuntu.com/">www.ubuntu.com</html>
[/HTML]

---

### Post by DoctorMO on 2008-08-11
Whoa, that's some serious javascript to do roll over effects... perhaps use css :hover modifier instead?

Not sure I want to help you though since a) wrong place for html help and b) Lots of things don't work in IE, c) and I hate IE.

---

### Post by mpgarate on 2008-08-11
i agree with the last two, and sorry its in the wrong place I wasnt sure where it should go

---

### Post by Delever on 2008-08-11
remove 

```

class="reflect"

```

from img tag. I don't even see such class linked or declared anywhere.

EDIT: Your Javascipt screws up your image. Just use simple link bellow or above image.

EDIT 2: I deserve a cookie.

---

### Post by LaRoza on 2008-08-11
Remove all the inline script. Use valid markup. And ask again.

---

### Post by mpgarate on 2008-08-11
thank you laroza now it works perfectly

---

### Post by Delever on 2008-08-11
Glad I could help.

(promises never ever bother again)

---

