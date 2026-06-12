---
title: "[fix] Server 8.04.1 Webmin 1.430 Bacula 2.2.8"
date: 2008-09-23
forum: Server Platforms
---

### Post by fade2gray on 2008-09-23
If you are unable to perform backups with the Webmin 'Bacula Backup System' module because of missing buttons etc. in 'Backup Jobs > Edit Backup Job', or because of an incomplete form in 'Run Backup Job', e.g. ...

[ [IMG]http://lh5.ggpht.com/fade2gray.uk/SNl9nniVVwI/AAAAAAAAAHg/7AC1nr6hfCE/s144/webmin_bacula.jpg[/IMG] ](http://picasaweb.google.co.uk/fade2gray.uk/Webmin?authkey=z9a-5vsimcM#5249364960258381570)

Make the following edits ...

Comment out the line [COLOR="DarkGreen"]**&close_console($h);**[/COLOR] in ...
/usr/share/webmin/bacula-backup/bacula-backup-lib.pl

```
# get_bacula_jobs()
# Returns a list of all jobs known to Bacula
sub get_bacula_jobs
{
local $h = &open_console();
local $jobs = &console_cmd($h, "show jobs");
# COMMENT OUT &close_console($h);
local @rv;
local $job;
foreach my $l (split(/\r?\n/, $jobs)) {
	if ($l =~ /^Job:\s+name=([^=]*\S)\s/) {
		$job = { 'name' => $1 };
		push(@rv, $job);
		}
	elsif ($l =~ /Client:\s+name=([^=]*\S)\s/ && $job) {
		$job->{'client'} = $1;
		}
	elsif ($l =~ /FileSet:\s+name=([^=]*\S)\s/ && $job) {
		$job->{'fileset'} = $1;
		}
	}
return @rv;
}
```

Add the lines of code where indicated in ...

/usr/share/webmin/bacula-backup/backup_form.cgi

```
[...]
print &ui_table_end();
print &ui_form_end([ [ "backup", $text{'backup_ok'} ] ]);

local $h = &open_console(); # CODE ADDED
&close_console($h); # CODE ADDED

&ui_print_footer("", $text{'index_return'});
```

and in ...

/usr/share/webmin/bacula-backup/edit_job.cgi

```
[...]
else {
	($bjob) = grep { $_->{'name'} eq $in{'name'} } &get_bacula_jobs();
	print &ui_form_end([ [ "save", $text{'save'} ],
			     ( $job->{'name'} eq 'Job' && $bjob ?
				( [ "run", $text{'job_run'} ] ) : ( ) ),
			     [ "delete", $text{'delete'} ] ]);
	}

local $h = &open_console(); # CODE ADDED
&close_console($h); # CODE ADDED

&ui_print_footer("list_jobs.cgi", $text{'jobs_return'});
```

Also, if you get an error along the lines of "bacula@localhost password=NO" when trying to run the backup job "BackupCatalog" (backup appears to complete suscessfully, but on restore produces a zero byte "bacula.sql" file), try the following edit.

Edit the line of code where indicated in ...

/etc/bacula/scripts/make_catalog_backup_awk

```
[...]
if (catname == cat1 || catname == cat2 || catname == cat3 || catname == cat4) {
	if (dbaddress == "") #Not optional in the case of MySQL
		dbaddress = "localhost"
              system("rm -rf /var/lib/bacula/.my.cnf")
              system("touch /var/lib/bacula/.my.cnf")
              system("chmod 600 /var/lib/bacula/.my.cnf")
	printf "[client]\n  host=%s\n  user=%s\n  password=%s\n",dbaddress,user,password >> "/var/lib/bacula/.my.cnf"
	if (dbport != "")
		printf "  port=%s\n",dbport >> "/var/lib/bacula/.my.cnf"
	if (dbsocket != "")
		printf "  socket=%s\n",dbsocket >> "/var/lib/bacula/.my.cnf"
# CHANGE THIS		system(sprintf ("mysqldump %s > /var/lib/bacula/bacula.sql",dbname))
	system(sprintf ("mysqldump --defaults-file=/var/lib/bacula/.my.cnf %s > /var/lib/bacula/bacula.sql",dbname)) # FOR THIS
}
[...]
```

HTH.

---

### Post by vaporflux on 2008-12-14
I can confirm that this worked for me- thanks fade2gray!

---

### Post by fghi906 on 2008-12-15
[align=left][align=left]*[size=9pt]Pearlove Jewelry Inc. lauches many fine pearl jewelries ?C pearl necklaces, pearl bracelets, pearl earrings, and fine Swarovski crystal jewelry for wedding bridal party, Christmas Eve, and other occasions. Detailed products lists are at [[color=#800080]http://www.pearlove.com/christmas-gift-jewelry-cl-49.html[/color]](http://www.pearlove.com/christmas-gift-jewelry-cl-49.html) . [/size]*[/align][/align][align=left][align=left][size=9pt] [/size][/align][/align][align=left][align=left][size=9pt]Pearlove.com, one of the most swiftly developing cultured pearl jewelry wholesalers in China, launches many new styles of freshwater pearl necklaces, bracelets, cultured pearl earrings and pearl jewelry sets, which can be worn in wedding parties, grand dinners, and etc.In the past few months, Pearlove.com specializes in designing fashion pearl jewelry, especially for Christmas. The styles of pearl necklaces include single-row simple necklaces, illusion necklaces, tin cup necklaces, lariat necklaces, multi-strand, twisted necklaces, rope necklaces and more.  Materials used are including various shapes and colors of freshwater pearls, Chinese semi-precious stones, Swarovski crystals, Chinese natural crystals and etc. [/size][/align][/align][align=left][align=left][size=9pt]The jewelries made for formal occasions are usually used with good quality pearls and stones, and light colors. For example, 925 silver chains & clasps, round or near round pearls are used for bridal jewelry styles, and the colors are usually white, pink or lavender. Most of these styles are simple and beautiful. Usually, pearl colors are changeable, according to buyers&#8217; own design.Pearl jewelry sets are popular with most clients. Consumers like more to wear a set jewelry which can match their clothes, hair and shoes perfectly. Pearlove&#8217;s jewelry sets are usually including necklaces and earrings, bracelets according clients request. The jewelry sets styles contain formal set, good quality set and fashion style, to meet different market. Clients can easily choose equal prices and styles on [[color=#0000ff]http://www.pearlove.com/pearl-jewelry-c-5.html[/color]](http://www.pearlove.com/pearl-jewelry-c-5.html) .[/size][/align][/align][align=left][align=left][size=9pt]About Pearlove.comPearlove Jewelry ([http://www.pearlove.com](http://www.pearlove.com)), freshwater pearl jewelries online wholesale store, mainly focused in Chinese natural colors of cultured freshwater pearls; Pearlove Jewelry also does some dyed pearls basing clients&#8217; requests. In addition, the company wholesale coral jewelry, turquoise, shell beaded jewelry, crystal and other gemstone jewelry. Customized requests are accepted as well. [/size][/align][/align]

---

### Post by Tim55555 on 2009-07-15
Worked for me too . . . Thanks very much fade2gray . . .

---

### Post by Thirtysixway on 2009-07-17
> **Tim55555 said:**
> Worked for me too . . . Thanks very much fade2gray . . .

Has this not been fixed yet? Perhaps someone should submit it as a bugfix... 1.430 was like 5 versions ago.

---

### Post by fade2gray on 2009-07-18
> **Thirtysixway said:**
> Has this not been fixed yet? Perhaps someone should submit it as a bugfix... 1.430 was like 5 versions ago.

No matter what version Webmin is, the Bacula Backup Sytem module was donated by [Linmin]("http://www.linmin.com/"), a Webmin supporter, who appears to no longer maintain it.

Although BBS is provided as part of the Webmin package, it is not listed as one of Webmin's "[Standard Modules]("http://www.webmin.com/standard.html")".

---

