---
title: "Help decrypting mix of b64/bz2 block."
date: 2012-07-29
forum: Ubuntu Dev Link Forum
---

### Post by Apollo93 on 2012-07-29
Hello, I was using a cheap form of encoding to basically prevent skiddish hackers or sneaky eyes who may be using my laptop from reading these files I created the following basic method for.. for some reason I'm now unable to decode this file only, all others are fine. If anyone is able to help me I'd appreciate it.

How I encoded the file..
```

    def encode(self, s):
        s = s[::-1]
        s = bz2.compress(s)
        s = base64.b64encode(s)
        self.s = s[::-1]
        return self.s

``````

vicfile = open(self.path, 'w')
            for line in struct._fields_:
                line = self.encode(line)
                vicfile.write(line)
                vicfile.write('\n')
            vicfile.close()

```and the file itself... [http://paste.ubuntu.com/1118368/](http://paste.ubuntu.com/1118368/)

---

