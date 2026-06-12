---
title: "The interwebs can read your mind."
date: 2010-05-21
forum: The Cafe
---

### Post by dragos240 on 2010-05-21
[SIZE=3]I was visiting my topic about an MCAS image macro I made, and I noticed the "At first I was like..... but then I lol'd" meme. I was also listening to music from doukutsu monogatari......

So I looked it up at know your meme. This happened:[/SIZE]
[IMG]http://knowyourmeme.com/i/000/047/529/original/AtfirstIwaslike.PNG?1272176257[/IMG]
[SIZE=2]
[SIZE=3]What do you know. It's balrog from doukutsu monogatari.[/SIZE][/SIZE]

[SIZE=1][COLOR=LemonChiffon]And here I thought ricemonster was the only one who could read my mind.[/COLOR][/SIZE]

---

### Post by Bachstelze on 2010-05-21
Right, now get back to work!

---

### Post by dragos240 on 2010-05-21
> **Bachstelze said:**
> Right, now get back to work!

It's the weekend here. It's my relaxing time.

---

### Post by baddog144 on 2010-05-21
Um. Ok then. *wanders off*

---

### Post by YuiDaoren on 2010-05-21
[FONT=Arial Black][SIZE=4]co· in· ci· dence[/SIZE][/FONT]&#8194;/ko&#650;&#712;&#618;n s&#618; d&#601;ns/
–noun

[LIST=1]
[*]a  striking occurrence of two or more events at one time apparently by mere  chance: Our meeting in Venice was pure  coincidence.
[*]the condition or fact of  coinciding.
[*]an instance of this.
[/LIST]

---

### Post by MaxIBoy on 2010-05-21
In unrelated news, I just optimized a loop from this:
```
    // try finding the variable
    cvar_get_prev = &chain;
    COMPUTE_HASH_KEY( cvar_get_hash_key , var_name , i );
    for (cvar_get_var = cvar_vars ; cvar_get_var && cvar_get_var->hash_key <= cvar_get_hash_key ; cvar_get_var=cvar_get_var->next)
    {
        if (cvar_get_var->hash_key == cvar_get_hash_key && !Q_strcasecmp (var_name, cvar_get_var->name))
        {
            cvar_get_var->flags |= flags;
            return cvar_get_var;
        }
        cvar_get_prev = &( cvar_get_var->next );
    }
```to this:
```
    // try finding the variable 
    COMPUTE_HASH_KEY( cvar_get_hash_key , var_name , i );
    cvar_get_var = chain;
    cvar_get_prev = chain;
    // "chain" (first entry) is always non-null but stores no value. 
    while ( cvar_get_var->next && cvar_get_var->next->hash_key < cvar_get_hash_key )
        cvar_get_var = cvar_get_var->next;

    cvar_get_prev = cvar_get_var;
    cvar_get_var = cvar_get_var->next;
    if (cvar_get_var){        
        if (cvar_get_var->hash_key == cvar_get_hash_key && !Q_strcasecmp (var_name, cvar_get_var->name)) { 
            cvar_get_var->flags |= flags; 
            return cvar_get_var;
        }
    }
```(changes needed elsewhere to handle cvar_get_prev differently) while having the same exact result. That loop is still 15% of the program's execution time (under certain very-specific conditions.) But it's a big improvement over 70% like it used to be!

---

### Post by JDShu on 2010-05-21
I still can't beat the hell level :(

---

### Post by undecim on 2010-05-21
> **JDShu said:**
> I still can't beat the hell level :(

I hacked Profile.dat for 9999 life and infinite missles to get through it, lol.

If I had the time to practice it, I know I could beat it legitimately, but I wanted to get through.

---

### Post by dragos240 on 2010-05-22
> **undecim said:**
> I hacked Profile.dat for 9999 life and infinite missles to get through it, lol.

If I had the time to practice it, I know I could beat it legitimately, but I wanted to get through.
Where can I get the .dat hoxxor? :P

---

### Post by juancarlospaco on 2010-05-22
ed
a
 " vim and emacs sux, ed ftw "
wq file.txt

---

