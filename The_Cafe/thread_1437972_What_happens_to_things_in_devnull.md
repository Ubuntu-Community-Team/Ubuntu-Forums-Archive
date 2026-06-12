---
title: "What happens to things in /dev/null?"
date: 2010-03-24
forum: The Cafe
---

### Post by swoll1980 on 2010-03-24
I'm reading a book, and I just don't get it. Why would you use it? What happens to stuff once it's in there? Does it get deleted when you restart? Can things be recovered from there?

---

### Post by tica vun on 2010-03-24
You can't put files into /dev/null. You can for example direct output of programs you don't want to see into it.

---

### Post by CptPicard on 2010-03-24
It's just something that you can redirect output to if you want it to be discarded. The whole point is that anything that goes there, is just ignored.

---

### Post by JSeymour on 2010-03-24
> **swoll1980 said:**
> I'm reading a book, and I just don't get it. Why would you use it?Suppose, for example, you wanted to run a "find" against a directory that you knew contained directories you weren't allowed to read.  Normally, "find" would grumble about the unreadable directories.  But if you do "2>/dev/null" (sending STDERR output to the bit-bucket), voila': No error messages cluttering things up.  There are many uses like that.

> **swoll1980 said:**
> What happens to stuff once it's in there?It does into a kind of "data purgatory," where daemons poke at it with pitchforks for all eternity.

> **swoll1980 said:**
> Does it get deleted when you restart?Actually, there's nothing to delete.  The /dev/null device simply discards it upon receipt :)

Jim

---

### Post by Simian Man on 2010-03-24
No, the point of it is that everything you send there is never written at all anywhere.  That's useful only when you just don't care about the stuff you send.  For example, the Kate text editor prints out a bunch of garbage on the command line.  So if you still want your terminal to be clean, you can start it like so:

```

kate 1>/dev/null 2>/dev/null &

```

The "1>/dev/null" redirects the stdout output to /dev/null and the "2>/dev/null" redirects stderr there.  The "&" of course runs it as a background process.  When I was trying out kate I aliased the kate command to do that automatically.

I'm sure others can think of other examples where having a dummy output location is helpful.

---

### Post by swoll1980 on 2010-03-24
so if I did something like 

```
cat /etc/resolv.conf > /dev/null
```

Would it delete the contents of resolv.conf or just not show me the contents?

---

### Post by tica vun on 2010-03-24
> **swoll1980 said:**
> so if I did something like 

```
cat /etc/resolv.conf > /dev/null
```Would it delete the contents of resolv.conf or just not show me the contents?

Think, does cat manipulate the file in any other way than printing its contents on the designated output? It doesn't, so using cat can't delete the file, no matter what the output is.

---

### Post by schauerlich on 2010-03-24
> **swoll1980 said:**
> so if I did something like 

```
cat /etc/resolv.conf > /dev/null
```

Would it delete the contents of resolv.conf or just not show me the contents?

It would not delete it.

---

### Post by Simian Man on 2010-03-24
It would essentially do nothing at all.

---

### Post by lykwydchykyn on 2010-03-24
You can redirect /dev/null INTO a file, which is an effective way of emptying a file without deleting it.  
e.g.
```

cat /dev/null > file_I_dont_care_about.really

```

I use that to empty log file sometimes, since deleting them and recreating them causes some programs to quit logging.

---

### Post by _h_ on 2010-03-24
It's the blackhole of *nix based systems.

---

### Post by diesch on 2010-03-24
> **lykwydchykyn said:**
> You can redirect /dev/null INTO a file, which is an effective way of emptying a file without deleting it.  
e.g.
```

cat /dev/null > file_I_dont_care_about.really

```I use that to empty log file sometimes, since deleting them and recreating them causes some programs to quit logging.

You can do that with any other empty file, too.

---

### Post by swoll1980 on 2010-03-24
so if I accidentally did it backwards;
```
cat /dev/null > /etc/resolv.conf 
```
It would make /etc/resolv.conf a blank document?

---

### Post by Simian Man on 2010-03-24
> **swoll1980 said:**
> so if I accidentally did it backwards;
```
cat /dev/null > /etc/resolv.conf 
```
It would make /etc/resolv.conf a blank document?

Yes.  For even more fun, try it with /dev/random :).

---

### Post by swoll1980 on 2010-03-24
Well I guess I should be careful with the things I'm trying to do then.

---

### Post by donkyhotay on 2010-03-24
> **Simian Man said:**
> [QUOTE=swoll1980;9021388]so if I accidentally did it backwards;
```
cat /dev/null > /etc/resolv.conf 
```
It would make /etc/resolv.conf a blank document?Yes.  For even more fun, try it with /dev/random :).[/QUOTE]

Please don't do either... your going to make some poor ubuntuforum user cry when you ask them to fix your system without reinstalling.

---

### Post by swoll1980 on 2010-03-24
> **Simian Man said:**
> Yes.  For even more fun, try it with /dev/random :).

Is there a set number of characters in the string it produces, or will it go on forever.

---

### Post by Penguin Guy on 2010-03-24
Putting something in [FONT="Courier New"]/dev/null[/FONT] is like talking to a brick wall - since it can't hear you, the information is simply gone.

---

### Post by swoll1980 on 2010-03-24
> **donkyhotay said:**
> Please don't do either... your going to make some poor ubuntuforum user cry when you ask them to fix your system without reinstalling.

resolv.conf is easily repairable. No worries.

---

### Post by Penguin Guy on 2010-03-24
> **swoll1980 said:**
> Is there a set number of characters in the string it produces, or will it go on forever.
It goes on forever.

---

### Post by swoll1980 on 2010-03-24
> **Penguin Guy said:**
> It goes on forever.

So other than cleaning a hard drive what would this be good for?

---

### Post by sisco311 on 2010-03-24
> **lykwydchykyn said:**
> You can redirect /dev/null INTO a file, which is an effective way of emptying a file without deleting it.  
e.g.
```

cat /dev/null > file_I_dont_care_about.really

```

I use that to empty log file sometimes, since deleting them and recreating them causes some programs to quit logging.

If you don't like to type too much, then: 
```
> /path/to/file
```
:evil:

> **swoll1980 said:**
> so if I accidentally did it backwards;
```
cat /dev/null > /etc/resolv.conf 
```
It would make /etc/resolv.conf a blank document?

Only if you are logged in as root, otherwise you have to run something like:

```
cat /dev/null | sudo tee /path/to/file
```or
```
echo | sudo tee /path/to/file
```
(some config files need a newline at the end ;) )

---

### Post by Simian Man on 2010-03-24
> **swoll1980 said:**
> So other than cleaning a hard drive what would this be good for?

I use it for testing that my programs don't fail hard no matter what retarded things the user types in.

---

### Post by whiskeylover on 2010-03-24
What happens in /dev/null stays in /dev/null

---

