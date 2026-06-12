---
title: "Can I Use X2Go?"
date: 2022-04-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2022-04-02
I look after a number of friends/neigbours machines and looking at moving away from Teamviewer to ssh/X2Go for remote working.  Reading that ecdsa is a better key than rsa I've set up a shh session between two machines using ecdsa keys - so far so good.  Now I read (although a lot of text is some years old) X2Go doesn't work with ecdsa - so I'm not sure where to go from here. Reverting to rsa seems an obvious choice, but as a non-professional working only with basic Desktop machines, it is hard for me to know how 'risky' it is to use rsa rather than ecdsa for the occasional connection.  Is it the case that in 2022 X2Go still does not work with ecdsa and should I go with rsa?

---

### Post by Quarkrad on 2022-04-02
Looks like I've posted in hast - it appears to work although based on what I've read I don't think it should. (Perhaps (obviously)I don't understand how ssh/X2Go works).  I've clicked on the X2Go session option *Try auto login (via SSH Agent or default SSH key)* and to my surprise the connection was made and I see the remote Desktop.  It looks like X2Go recognised my ssh/ecdsa  config.

---

### Post by him610 on 2022-04-02
Yes, you can use x2go.

I occasionally use it myself.

Biggest advocate for x2go is TheFU who can probably answer your questions better than I. He normally is on line, but this being Saturday down in Squidbilly Land, he is probably out for the day.
Just be patient, he will probably be back on line tomorrow.

---

