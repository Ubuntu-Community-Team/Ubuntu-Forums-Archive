---
title: "Slow performing search on big directories, 12.04 Office NAS"
date: 2014-04-29
forum: Server Platforms
---

### Post by Misterbadexample on 2014-04-29
I have a re-purposed old Dell running 12.04 server. We're mostly using it as a NAS and we have an art department using Mac OS X and most of our other departments using Windows 7 or 8. My problem is this--we have to search and find a lot of files, particularly larger art files, and there is one huge directory in particular that is very slow.

The art department is using a tool called EasyFind to search over the LAN. I doubt that I can train everyone to use locate in their terminal but doing a search in the browser is not a bad possibility if any exists.

Any words of wisdom of how to help speed up this janky machine?

---

### Post by SeijiSensei on 2014-04-29
[Sphinx]("http://sphinxsearch.com/") is blazingly fast, but it expects to find an SQL database or similar data source for the searches.  You could run a script that runs from cron to scan the directories and update the database routinely, say once per hour.  You wouldn't need much other than the full directory path for each entry, though if you wanted to make the service more powerful, you could build a web front-end where the designers could register their files and include additional text comments that would also be searchable.  You don't need an SQL backend; Sphinx can use a [tab-delimited file]("http://sphinxsearch.com/docs/2.2.2/tsvpipe.html") as a data source as well.

I run a couple dozen listservers for a client, all of which can be browsed and searched over the web.  I've got just under 200K documents in the database.  Sphinx returns full-text search results for this application in well under a second.

---

### Post by Misterbadexample on 2014-04-29
That sounds exactly like the kind of solution I need, but it's a bit beyond my current skillset. When I saw that [FONT=Courier New]locate[/FONT] and [FONT=Courier New]updatedb[/FONT] work the way they do it made sense to have a cron script running like you're saying. But this seems better at solving the problem.

I'll look deeper into Sphinx--I just know that I'm still an entry level Linux admin. I have manually set up an SQL db before, but that was only for Wordpress. I imagine it's similar? Setting up a database and allowing the software to use it as it sees fit? If Sphinx has good documentation I can probably dummy my way through all of these things you're saying.

Does it come with any sort of basic web/intranet frontend? Or would one have to be created the way you describe?

---

### Post by Misterbadexample on 2014-04-29
I'm seeing a Wordpress and also Drupal plugin section. I assume that I could use these ostensibly as the browser front end you're talking about? Set up one of these to be an intranet search and use these plugins? If that's the case this is really cool software.

---

### Post by tgalati4 on 2014-04-29
What are the specifications of the old Dell machine?  Perhaps it needs more RAM to improve the performance of the searches or a faster disk like SSD for the OS and a RAID for the data files.  

Since these are art files (presumably graphic arts) perhaps run a gallery:  [http://gallery2.org](http://gallery2.org)

---

### Post by Misterbadexample on 2014-04-29
Thanks for the reply, tgalati4,

IMHO it could use an SSD and a raid to speed up the performance, to say nothing of more memory. But that's sort of the nuclear option. This thing is built from garbage and spare parts as it is. It is basically a re-purposed XP box downgraded from Vista to give you an idea of when we bought it. SeijiSensei's suggestion of SQL indexing search is pretty much exactly the solution I need--I just hope I've got the time and grit to learn how to implement it.

Gallery looks like really cool software. I'm sure I could use it for something, but a lot of these are production art files. Some of them are only readable by proprietary programs.

---

### Post by SeijiSensei on 2014-04-29
Sphinx comes with a PHP and a Python API ("application programming interface") that let's you access its server with well-defined function calls.   Here's a quick overview of how it works for me.  (This is on CentOS 6.5; some of the file locations might be different in Ubuntu.)  I'm using the RPM package for [Sphinx 2.2.2-beta on the Sphinx website]("http://sphinxsearch.com/downloads/beta/").  There are Ubuntu packages as well for the most recent versions, or you can install the **sphinxsearch** package from the Ubuntu repositories.

I have a configuration file as /etc/sphinx/sphinx.conf:
```

source mysearch
{
        type                    = pgsql

        sql_host                = localhost
        sql_user                = myuser
        sql_pass               = mypass
        sql_db                  = MyPostgreSQLDB
        sql_port                = 5432

# get the messages from the database
        sql_query               = SELECT msgid, subject, body, listid, unixdate, author_id FROM messages

# each message belongs to one of twenty listservers identified by listid
# also index on authors and the date the message was posted
        sql_attr_uint           = listid
        sql_attr_uint           = author_id
        sql_attr_timestamp      = unixdate

}


index mysearch
{
        source                  = mysearch
        path                    = /var/lib/sphinx/mysearch
        docinfo                 = extern
        #charset_type           = sbcs
        stopwords               = /etc/sphinx/stopwords
}

indexer
{
        mem_limit               = 128M
}


# stuff below pretty much boiler-plate
searchd
{
        listen                  = 9312
        log                     = /var/log/sphinx/searchd.log
        query_log               = /var/log/sphinx/query.log
        read_timeout            = 5
        max_children            = 30
        pid_file                = /var/lib/sphinx/searchd.pid
        max_matches             = 1000
        seamless_rotate         = 1
        preopen_indexes         = 1
        unlink_old              = 1
#       compat_sphinxql_magics  = 0
        workers                 = threads # for RT to work
        binlog_path             = /var/lib/sphinx
}

```
The first two stanzas define a data source and the index.  There are two more stanzas that control the two programs that are part of Sphinx.  One is a stand-alone indexer program which runs from cron, and the other a daemon called searchd that is started at boot.  

In the PHP script that runs the search, I have code like this:
```

        $spx = new SphinxClient ();

        $mode = SPH_MATCH_ALL;
        $ranker = SPH_RANK_PROXIMITY_BM25;

        $spx->SetServer ( $host, $port );
        $spx->SetConnectTimeout ( 1 );
        $spx->SetArrayResult ( true );
        $spx->SetFieldWeights ( $weights );
        $spx->SetRankingMode ( $ranker );
        $spx->SetFilter('listid',array($listid),FALSE);
        
        $res = $spx->Query ( $query, $index );

```
The first line creates a client object from the API file loaded earlier.  Then a bunch of defaults are set and the query run with the $spx->Query() function.  The "$query" variable contains the search text and the "$index" variable tells Sphinx which database to use; in this case $index would be set to "mysearch" to match the configuration file above.

Sphinx returns an array of ID numbers sorted according to the parameter you specified.  I let my users choose to search by relevance (the default), or by youngest to oldest or vice versa.  I then pass the array to another PHP script that displays the list of matching messages.

In the 2.1 versions, Sphinx also came with a simple command-line client called search.  It's not included in 2.2, so you might want to stick with the 2.1.7 release.  It might be an easier solution to program around than using the full API.

---

### Post by nerdtron on 2014-04-29
I think the client machines are the bottleneck here. I noticed on one of my windows pc if I have a local folder that has large files on it (especially pictures, .tiff and .psd) the windows explorer would take minutest to load the directory.
I'm guessing the client PC are having a hard time producing thumbnails, not to mention they also need to generate some sort of summary report on the folder itself.

---

### Post by Misterbadexample on 2014-04-30
Hey, Nerdtron. Excellent username, BTW.

Client machines DEFINITELY have a lot to do with it. The slowest performance is listing big directories on the macs, which have problems with slow performance over SMB2. I think that searching over a browser may help us sidestep that a bit--at least for FINDING files.

---

