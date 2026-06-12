---
title: "Quickly. Display sqlite3 inside treeview or component like this."
date: 2012-12-12
forum: Ubuntu Application Development
---

### Post by bogdannix on 2012-12-12
Sorry for so stupid question, I'm a noob in Ubuntu(and Linux at all, but not Windows) programming. I desided to use Quickly. So, I need to display sqlite3 DB inside treeview or component like this.(To work with choosen element then). I found design to print BD in terminal:
```
with self.hardbase:
            cur = self.hardbase.cursor()
            cur.execute("SELECT * FROM HardTable") 
            while True:
                row = cur.fetchone()
                if row == None:
                    break
                print row[0], row[1], row[2]
        cur.close()
```
But, how to display it inside GTK GUI? :-(
I need it done in maybe an hour or I'll RIP 
Thanks a lot for your complete for noobies answers!

---

