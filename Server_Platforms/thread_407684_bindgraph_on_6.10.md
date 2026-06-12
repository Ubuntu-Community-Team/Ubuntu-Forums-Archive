---
title: "bindgraph on 6.10"
date: 2007-04-12
forum: Server Platforms
---

### Post by brian-bonnier on 2007-04-12
Is anyone using bindgraph from the universe repository?  I have installed it on a few servers and cannot get it to function correctly.  The bind servers are logging querylog like the readme said to do.  the rrd is being created but the images do not.  Bindgraph creates the ,cgi-bin,bindgraph.cgi directory and it has web server permissions, the cgi loads with no images.  If i view the image i get an error like: 

ERROR: RRDs::graph(/var/cache/bindgraph/,cgi-bin,bindgraph.cgi/bindgraph_0.png.tmp, ...): Garbage ': Thu Apr 12 17:00:00 2007    graph created on Thu Apr 12 13:02:02 2007\r' after command:
COMMENT:last update: Thu Apr 12 17:00:00 2007    graph created on Thu Apr 12 13:02:02 2007\r

if i try to view the image directly.

the /var/cache/bindgraph/,cgi-bin,bindgraph.cgi/bindgraph_0.png.tmp does not exist but /var/cache/bindgraph/,cgi-bin,bindgraph.cgi directory does and I set the permissions to all write to eliminate permission error.

any suggestions on how to get this working?

Thanks
Brian

---

### Post by mflage on 2007-12-14
> **brian-bonnier said:**
> ERROR: RRDs::graph(/var/cache/bindgraph/,cgi-bin,bindgraph.cgi/bindgraph_0.png.tmp, ...): Garbage ': Thu Apr 12 17:00:00 2007    graph created on Thu Apr 12 13:02:02 2007\r' after command:
COMMENT:last update: Thu Apr 12 17:00:00 2007    graph created on Thu Apr 12 13:02:02 2007\r

Sorry for the late answer. I was desperately looking for the solution myself, until I decided to fix it myself..

Problem is in the perl code that should generate this graph. Problem is that you have to escape ':' for rrdtool. If not it interprets this as a new line of command and everything gets ****** up. Looking at mailgraph.cgi (which bindgraph.cgi) derives from, you can see this clearly. Try the following code snippet instead:

```

        my $lastupdate = localtime(last_update($rrd));
        my $created = localtime(time);

        $lastupdate =~ s|:|\\:|g unless $RRDs::VERSION < 1.199908;
        $created =~ s|:|\\:|g unless $RRDs::VERSION < 1.199908;

        my ($text, $xs, $ys) = RRDs::graph(
                $file,
                '--imgformat', 'PNG',
                '--width', $xpoints,
                '--height', $ypoints,
                '--start', '-' . $range,
                '--end', '-' . int($range * 0.01),
                '--vertical-label', 'queries/second',
                '--title', $title,
                '--lazy',
                @rrdef,
                @rrprint,
                'COMMENT:\s',
                "COMMENT: data updated\\: $lastupdate" . '\r',
                "COMMENT:graph created\\: $created" . '\r',
        );

```

This is just a dirty hack and should probably be prettified some before being submitted to the repositories - but it works.

Try that and see what happens.

---

