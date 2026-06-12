---
title: "Got a problem"
date: 2010-11-29
forum: The Cafe
---

### Post by Zerocool Djx on 2010-11-29
I got a "document" that is a .CSV file and cuts out cause open office program can't handle it. The file size is like 150mb so it aint't that big, but yet it is. 

Don't ask what it's for,... I just need a better program if anyone knows..

---

### Post by Mr. Picklesworth on 2010-11-29
Well, you could try Gnumeric. It *is* the better spreadsheet app, after all :b
Not sure if it's that hardy, though. A 150 MB CSV is pretty gigantic. You may need to bite the bullet and work with a custom tuned solution. (Like parsing the file with a Python script).

---

### Post by RiceMonster on 2010-11-29
a 150 MB csv? :eek:

---

### Post by czr114 on 2010-11-29
What are you looking to do?

This might be a job for a DB and a generic frontend.

---

### Post by RiceMonster on 2010-11-29
> **czr114 said:**
> What are you looking to do?

This might be a job for a DB and a generic frontend.

If you were going to put the data into mysql or something, you'd want to write a perl script or something similar to convert everything to insert queries. Wouldn't be all that hard.

---

### Post by Zerocool Djx on 2010-11-29
Is Gnumeric a Linux app? if so will it work in a VM?

---

### Post by Zerocool Djx on 2010-11-29
> **RiceMonster said:**
> If you were going to put the data into mysql or something, you'd want to write a perl script or something similar to convert everything to insert queries. Wouldn't be all that hard.

Actually I have a mysql of the same data,.. would that be easier? I don't know perl :(

---

### Post by jerenept on 2010-11-29
> **Zerocool Djx said:**
> Actually I have a mysql of the same data,.. would that be easier? I don't know perl :(

Uh, yes, using a database makes a million times more sense.

---

### Post by Zerocool Djx on 2010-11-29
> **jerenept said:**
> Uh, yes, using a database makes a million times more sense.


Wampserver?

---

### Post by czr114 on 2010-11-29
> **RiceMonster said:**
> If you were going to put the data into mysql or something, you'd want to write a perl script or something similar to convert everything to insert queries. Wouldn't be all that hard.

Depending on how simple the requirements are, he might be able to use MySQL and phpmyadmin.

That would handle the import and the operations, if he knows a bit of SQL, or can use the (albeit limited) find function.

---

### Post by czr114 on 2010-11-29
> **Zerocool Djx said:**
> Actually I have a mysql of the same data,.. would that be easier? I don't know perl :(

What do you need to do with the data?

---

### Post by Zerocool Djx on 2010-11-30
> **czr114 said:**
> What do you need to do with the data?

Just read it...


I got wampserver fired up,.. I know how to use phpmyadmin,.. I just haven't in a while..

---

### Post by RiceMonster on 2010-11-30
> **Zerocool Djx said:**
> Actually I have a mysql of the same data,.. would that be easier? I don't know perl :(

Yes. I just recommended perl to convert the data into queries, since perl is great for parsing text. If you already have the database, use that.

Since, I was bored, I wrote a script (which I haven't tested the inserts on). You could do something similar to this:

```

#!/usr/bin/perl

use warnings;
use strict;

open FH, "<data.csv" or die $!;
open  OUTFILE, ">insert_data.sql" or die $!;

while (<FH>) {
	
	chomp;
	my @array = split (/,/);
	
	# THE BELOW WON'T WORK IF THERE'S NUMERIC OR BOOLEAN VALUES
	# You would have to handle said fields differently
	foreach (@array) {
		$_ = "'$_'";
	}
	
	my $outstr = "INSERT INTO table_name (One,Two,Three,Four) VALUES (". join(",",@array) . ");\n";
	
	print OUTFILE $outstr;
}

close FH;
close OUTFILE;

```

---

### Post by Zerocool Djx on 2010-11-30
yes there is numaric values,..

I installed wampserver however I cannot get the localhoast myphpadmin to show up.. any guesses? yes I is using win 7 here... Sorry, but now isn't the time to be picky cause of what the data is..

---

### Post by Zerocool Djx on 2010-11-30
> **Zerocool Djx said:**
> yes there is numaric values,..

I installed wampserver however I cannot get the localhoast myphpadmin to show up.. any guesses? yes I is using win 7 here... Sorry, but now isn't the time to be picky cause of what the data is..

NM,.. I got it,.. skype was sharing the same PID

update:

Wampserver is a no go,. file to large..

---

### Post by smellyman on 2010-11-30
3.9 million pages? 150 mb? 
 
I am surprised you were able to get it that big. I would think MS office would choke on that too.
 
I assume this was an export from a databse?

---

### Post by czr114 on 2010-11-30
> **Zerocool Djx said:**
> NM,.. I got it,.. skype was sharing the same PID

update:

Wampserver is a no go,. file to large..

You need to change the max upload size and max post size in your php.ini.

You will also want to raise the max execution time.

---

### Post by HermanAB on 2010-11-30
Use Gnumeric for that.

---

### Post by Zerocool Djx on 2010-11-30
Yes, this is a very large database,.. this is just one of them too...

> **czr114 said:**
> You need to change the max upload size and max post size in your php.ini.

You will also want to raise the max execution time.

How do I do this?


Where do I get Gnumeric?

---

### Post by juancarlospaco on 2010-11-30
what it's for?

---

### Post by cariboo on 2010-11-30
Gnumeric is in the repositories. You can use the Software Center, the command line or Synaptic Package Manager to install it.

---

### Post by Zerocool Djx on 2010-11-30
> **juancarlospaco said:**
> what it's for?

Read the posts,.. that's all I can say..

---

### Post by juancarlospaco on 2010-11-30
> **Zerocool Djx said:**
> Read the posts,.. that's all I can say..
[http://en.wikipedia.org/wiki/Irony](http://en.wikipedia.org/wiki/Irony)
:)

Use a python script.

---

### Post by KiwiNZ on 2010-12-01
As you are not prepared to give information I am going to close this thread. We cannot be sure that we are not assisting in illegal activity.Sorry.

---

