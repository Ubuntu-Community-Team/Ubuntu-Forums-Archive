---
title: "Who can shorten this command?"
date: 2011-06-02
forum: The Cafe
---

### Post by Legendary_Bibo on 2011-06-02
I was bored because I couldn't fall asleep (still can't actually) so I bugged around with the sensors command, and I just wanted it to print out the the temperature from the virtual device, not the PCI sensor, and nothing more (it's more accurate).

```
sensors -A > sensorinfo3 && cat sensorinfo3 | cut -f2 -d'+' > sensorinfo4 && sed -n 2p sensorinfo4 > sensorinfo5 && cat sensorinfo5 | cut -c1-7
```

I then made is into a shell script and wrote an alias in my bashrc file so that 'sensors' would redirect to this script instead.

---

### Post by VCoolio on 2011-06-02
Maybe post the output of "sensors -A" and indicate what part you want. You can do something like this (replace "string" with a string that is unique to the line your info is in, and replace "3" with the right number to get your value:```
sensors -A | awk '/string/ { print $3 }'
```

---

### Post by amauk on 2011-06-02
> **Legendary_Bibo said:**
> ```
sensors -A > sensorinfo3 && cat sensorinfo3 | cut -f2 -d'+' > sensorinfo4 && sed -n 2p sensorinfo4 > sensorinfo5 && cat sensorinfo5 | cut -c1-7
```Just a note
You're using a lot of unnecessary temporary files in the above

If you rewrite it to use pipes instead, it'll be shorter, more efficient, and you won't have lots of temporary files lying around
```
sensors -A | cut -f2 -d'+' | sed -n 2p | cut -c1-7
```

(Efficiency is probably not noticeable on this script, but on anything more substantial, it'll be noticeably quicker)

---

