---
title: "Solr+Nutch on Ubuntu Server 10.04 (Lucid)"
date: 2010-07-16
forum: Server Platforms
---

### Post by guneza on 2010-07-16
I spent two days gathering information on which FOSS search engine and web crawler I should use for my company's internal search, and concluded with the combination of:

* Solr 1.4 (advanced search engine)
* Nutch 1.1 (search engine with a highly configurable crawler)

This HOWTO is updated to match ubuntu 10.04 based on the work of Sami Siren at Lucid Imagination available here: [http://www.lucidimagination.com/blog/2009/03/09/nutch-solr/](http://www.lucidimagination.com/blog/2009/03/09/nutch-solr/)

[SIZE="5"]Overview[/SIZE]
This HOWTO consists of the following:
[LIST=1]
[*]Installing Solr
[*]Installing Nutch
[*]Configuring Solr
[*]Configuring Nutch
[*]Crawling your site
[*]Indexing our crawl DB with solr
[*]Search the crawled content in Solr
[/LIST]

Allright, 'nough talk. Let's get down to it!

[size="5"]Prerequisites[/size]
I'll assume that you have an Ubuntu 10.04 server installed and that you are logged in as root whilst working on this.
```

$ sudo su -
#
```

[size="5"]Installing Solr[/size]
Luckily, solr 1.4 is present in APT!

```
# apt-get install solr-common solr-tomcat tomcat6
```

[size="5"]Installing Nutch[/size]
Go to a proper working directory, download and unpack Nutch:
```

# cd /tmp
# wget [http://mirrorservice.nomedia.no/apache.org/nutch/apache-nutch-1.1-bin.tar.gz](http://mirrorservice.nomedia.no/apache.org/nutch/apache-nutch-1.1-bin.tar.gz)
# cd /usr/share
# tar zxf /tmp/apache-nutch-1.1-bin.tar.gz
# ln -s apache-nutch-1.1-bin nutch

```

[size="5"]Configuring Solr[/size]
For the sake of simplicity we are going to use the example configuration of Solr as a base.

Back up the original file:
```

# mv /etc/solr/conf/schema.xml /etc/solr/conf/schema.xml.orig 

```

And replace the Solr schema with the one provided by Nutch 
```

# cp /usr/share/nutch/conf/schema.xml /etc/solr/conf/schema.xml 

```

Now, we need to configure Solr to create snippets for search results.

Edit /etc/solr/conf/schema.xml and change the following line:
```

<field name="content" type="text" **stored="false"** indexed="true"/>

```

To this:
```

<field name="content" type="text" **stored="true"** indexed="true"/>

```

Create a new dismax request handler, to enabling relevancy tweaks.

Back up the original file:
```

# cp /etc/solr/conf/solrconfig.xml /etc/solr/conf/solrconfig.xml.orig 

```

Add the following fragment to _/etc/solr/conf/solrconfig.xml_:

```

  <!-- GZR: 2010-07-15 Added to integrate with Nutch crawler.
  -->
  <requestHandler name="/nutch" class="solr.SearchHandler" >
    <lst name="defaults">
      <str name="defType">dismax</str>
      <str name="echoParams">explicit</str>
      <str name="tie">0.01</str>
      <str name="qf">
        content^0.5 anchor^1.0 title^1.2
      </str>
      <str name="pf">
        content^0.5 anchor^1.5 title^1.2 site^1.5
      </str>
      <str name="fl">
        url
      </str>
      <str name="mm">
        2&lt;-1 5&lt;-2 6&lt;90%
      </str>
      <str name="ps">100</str>
      <str name="hl">true</str>
      <str name="q.alt">*:*</str>
      <str name="hl.fl">title url content</str>
      <str name="f.title.hl.fragsize">0</str>
      <str name="f.title.hl.alternateField">title</str>
      <str name="f.url.hl.fragsize">0</str>
      <str name="f.url.hl.alternateField">url</str>
      <str name="f.content.hl.fragmenter">regex</str>
    </lst>
  </requestHandler>

```


Now, restart Tomcat:
```

# service tomcat6 restart

```

It is a good idea to tail -f the tomcat files and ensure that there are no errors.

[size="5"]Configuring Nutch[/size]
Go into the nutch directory and do all the work from there:
```

cd /usr/share/nutch

```

Edit conf/nutch-site.xml and add the following in between the <configuration>-clauses: 

```

  <property>
    <name>http.robots.agents</name>
    <value>nutch-solr-integration-test,*</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.name</name>
    <value>nutch-solr-integration-test</value>
    <description>FreeCode AS Robots Name</description>
  </property>
  <property>
    <name>http.agent.description</name>
    <value>FreeCode Norway Web Crawler using Nutch 1.0</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.url</name>
    <value>http://www.freecode.no/</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.email</name>
    <value>[COLOR="Red"]YOUR EMAIL ADDRESS HERE[/COLOR]</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.version</name>
    <value></value>
    <description></description>
  </property>
  <property>
    <name>generate.max.per.host</name>
    <value>100</value>
  </property>

```

I need to ensure that the crawler does not leave our domain, otherwise I would end up crawling the entire Internet.

I inserted our domain into _conf/regex-urlfilter.txt:
```

# allow urls in freecode.no domain
+^[http://(](http://()[a-z0-9\-A-Z]*\.)*freecode.no/
 
# deny anything else
-.

```

Now, we need to instruct the crawler where to start crawling, so create a seed list:
```

# mkdir urls
# echo "http://www.freecode.no/" > urls/seed.txt

```

[size="5"]Crawling your site[/size]
Let's start crawling!

Start by injecting the seed url(s) to the nutch crawldb:
```

# bin/nutch inject crawl/crawldb urls

```

Next, generate fetch list:
```

# bin/nutch generate crawl/crawldb crawl/segments

```

The above command generated a new segment directory under /usr/share/nutch/crawl/segments that contains the urls to be fetched. All following commands require accessing the latest segment directory as their main parameter so we&#8217;ll store it in an environment variable:
```

export SEGMENT=crawl/segments/`ls -tr crawl/segments|tail -1`

```

Launch the crawler!
```

bin/nutch fetch $SEGMENT -noParsing

```

And parse the fetched content:
```

bin/nutch parse $SEGMENT

```

Now we need to update the crawl database to ensure that for all future crawls, Nutch only cheks the already crawled pages, and only fetches new and changed pages.
```

bin/nutch updatedb crawl/crawldb $SEGMENT -filter -normalize

```

Create a link database:
```

bin/nutch invertlinks crawl/linkdb -dir crawl/segments

```

Now a full Fetch cycle is completed. I have created a script to simplify the crawl job:
```

#!/bin/bash

# short script to help crawl

unset SEGMENT

# set this to your nutch home dir
NUTCH_HOME="/usr/share/nutch"

cd ${NUTCH_HOME}

${NUTCH_HOME}/bin/nutch generate crawl/crawldb crawl/segments
[ $? = 0 ] || { echo "An error occured while generating the fetch list!"; exit $?; }

export SEGMENT=crawl/segments/`ls -tr crawl/segments|tail -1`
${NUTCH_HOME}/bin/nutch fetch $SEGMENT -noParsing
[ $? = 0 ] || { echo "An error occured while FETCHING the content!"; exit $?; }

${NUTCH_HOME}/bin/nutch parse $SEGMENT
[ $? = 0 ] || { echo "An error occured while PARSING the content!"; exit $?; }

${NUTCH_HOME}/bin/nutch updatedb crawl/crawldb $SEGMENT -filter -normalize
[ $? = 0 ] || { echo "An error occured while updating the crawl DB!"; exit $?; }

${NUTCH_HOME}/bin/nutch invertlinks crawl/linkdb -dir crawl/segments
[ $? = 0 ] || { echo "An error occured while creating link database!"; exit $?; }

# success!
exit 0

#EOF

```

[size="5"]Indexing our crawl DB with solr[/size]
```

bin/nutch solrindex [http://127.0.0.1:8080/solr/](http://127.0.0.1:8080/solr/) crawl/crawldb crawl/linkdb crawl/segments/*

```

[size="5"]Search the crawled content in Solr[/size]
Now the indexed content is available through Solr. You can try to execute searches from the Solr admin ui from
```

[http://127.0.0.1:8080/solr/admin](http://127.0.0.1:8080/solr/admin)

```

or directly with url like:
```

[http://127.0.0.1:8080/solr/nutch/?q=kurs&amp;version=2.2&amp;start=0&amp;rows=10&amp;indent=on&amp;wt=json](http://127.0.0.1:8080/solr/nutch/?q=kurs&amp;version=2.2&amp;start=0&amp;rows=10&amp;indent=on&amp;wt=json)

```

---

### Post by plunder on 2010-08-01
this guide is excellent, I followed it exactly and got it running. Thank you for that.

I want to add, that I needed to add

cd $NUTCH_HOME; after the variable was declared to get the crawl script running on my machine.

Great guide thanks again!

---

### Post by khatkarrohit on 2010-09-13
This tutorial rocks..........Its working for me too.

---

### Post by guneza on 2010-09-23
> **plunder said:**
> this guide is excellent, I followed it exactly and got it running. Thank you for that.

I want to add, that I needed to add

cd $NUTCH_HOME; after the variable was declared to get the crawl script running on my machine.

Great guide thanks again!

Glad I could help. :) 

I've added the cd command as you suggested.

Thanks!

---

### Post by Tomer T on 2010-12-01
This guide is really great but...
I followed the instructions exactly and something went wrong along the way.
I managed to fetch the url's but I cant search with Solr. each search returns me:
"This XML file does not appear to have any style information associated with it. The document tree is shown below."

And than:
"
<response>
&#8722;
<lst name="responseHeader">
<int name="status">0</int>
<int name="QTime">12</int>
&#8722;
<lst name="params">
<str name="q">kurs</str>
<str name="amp;start">0</str>
<str name="amp;wt">json</str>
<str name="amp;version">2.2</str>
<str name="amp;indent">on</str>
<str name="amp;rows">10</str>
</lst>
</lst>
<result name="response" numFound="0" start="0"/>
<lst name="highlighting"/>
</response>
"

I don't understand why cause all the link commands were fine and i saw the crawler fetching the url's...
pls Help me 
Thanks a lot

---

### Post by gineta on 2010-12-02
Hi I have Ubuntu 10.10 with Nutch Solr and Tomcat 
But In the search page of tomcat6 after search I get a Blank Page
In Tomcat logs
I get (See down) --- Any Idea why I get this problem? Thanks in advance ;)
> 02-Dec-2010 10:57:43 org.apache.catalina.core.StandardWrapperValve invoke
SEVERE: Servlet.service() for servlet jsp threw exception
java.lang.NullPointerException
        at org.apache.nutch.searcher.FetchedSegments.getSummary(FetchedSegment$
        at org.apache.nutch.searcher.FetchedSegments$SummaryTask.call(FetchedS$
        at org.apache.nutch.searcher.FetchedSegments$SummaryTask.call(FetchedS$
        at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:303)
        at java.util.concurrent.FutureTask.run(FutureTask.java:138)
        at java.util.concurrent.ThreadPoolExecutor$Worker.runTask(ThreadPoolEx$
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecut$
        at java.lang.Thread.run(Thread.java:662)

---

### Post by gineta on 2010-12-05
HI I believe I solve the problem 
The problem is in many forums and not any solution become solve with the next:

In tomcat example ubuntu: /var/lib/tomcat6
we need to change the user of teh aplication nutch 
example if is ROOT we change sudo chown -R nutch:tomcat6

After that we esit with nano the next
nano /var/lib/tomcat6/webapps/ROOT/WEB-INF/classes/nutch-default.xml

and we solve the correct path
*> <property>
**<name>searcher.dir</name>
****<value>/nutch/src/apache-nutch/crawl</value>
You put the path of your aplication nutch

At the end all that configuration need to work

For crawl and index for tomcat we use this script 
you change the paths according to your server

>  Runs the Nutch bot to crawl or re-crawl
# Usage: bin/runbot [safe]
#        If executed in 'safe' mode, it doesn't delete the temporary
#        directories generated during crawl. This might be helpful for
#        analysis and recovery in case a crawl fails.
#
# Author: Susam Pal



You can get a Idea full script here [http://wiki.apache.org/nutch/Nutch_0.9_Crawl_Script_Tutorial](http://wiki.apache.org/nutch/Nutch_0.9_Crawl_Script_Tutorial)

OK With that the server nee to work fine and not more blank pages in Tomcat Search. The problem is not of memory how means in many forums is a problem of how is make the Index The script of Susan work perfect in Nutch 1.2

any problems only ask :p :popcorn:

---

### Post by broomie on 2010-12-08
> **guneza said:**
> I spent two days gathering information on which FOSS search engine and web crawler I should use for my company's internal search, and concluded with the combination of:

* Solr 1.4 (advanced search engine)
* Nutch 1.1 (search engine with a highly configurable crawler)

This HOWTO is updated to match ubuntu 10.04 based on the work of Sami Siren at Lucid Imagination available here: [http://www.lucidimagination.com/blog/2009/03/09/nutch-solr/](http://www.lucidimagination.com/blog/2009/03/09/nutch-solr/)

[SIZE="5"]Overview[/SIZE]
This HOWTO consists of the following:
[LIST=1]
[*]Installing Solr
[*]Installing Nutch
[*]Configuring Solr
[*]Configuring Nutch
[*]Crawling your site
[*]Indexing our crawl DB with solr
[*]Search the crawled content in Solr
[/LIST]

Allright, 'nough talk. Let's get down to it!

[size="5"]Prerequisites[/size]
I'll assume that you have an Ubuntu 10.04 server installed and that you are logged in as root whilst working on this.
```

$ sudo su -
#
```

[size="5"]Installing Solr[/size]
Luckily, solr 1.4 is present in APT!

```
# apt-get install solr-common solr-tomcat tomcat6
```

[size="5"]Installing Nutch[/size]
Go to a proper working directory, download and unpack Nutch:
```

# cd /tmp
# wget [http://mirrorservice.nomedia.no/apache.org/nutch/apache-nutch-1.1-bin.tar.gz](http://mirrorservice.nomedia.no/apache.org/nutch/apache-nutch-1.1-bin.tar.gz)
# cd /usr/share
# tar zxf /tmp/apache-nutch-1.1-bin.tar.gz
# ln -s apache-nutch-1.1-bin nutch

```

[size="5"]Configuring Solr[/size]
For the sake of simplicity we are going to use the example configuration of Solr as a base.

Back up the original file:
```

# mv /etc/solr/conf/schema.xml /etc/solr/conf/schema.xml.orig 

```

And replace the Solr schema with the one provided by Nutch 
```

# cp /usr/share/nutch/conf/schema.xml /etc/solr/conf/schema.xml 

```

Now, we need to configure Solr to create snippets for search results.

Edit /etc/solr/conf/schema.xml and change the following line:
```

<field name="content" type="text" **stored="false"** indexed="true"/>

```

To this:
```

<field name="content" type="text" **stored="true"** indexed="true"/>

```

Create a new dismax request handler, to enabling relevancy tweaks.

Back up the original file:
```

# cp /etc/solr/conf/solrconfig.xml /etc/solr/conf/solrconfig.xml.orig 

```

Add the following fragment to _/etc/solr/conf/solrconfig.xml_:

```

  <!-- GZR: 2010-07-15 Added to integrate with Nutch crawler.
  -->
  <requestHandler name="/nutch" class="solr.SearchHandler" >
    <lst name="defaults">
      <str name="defType">dismax</str>
      <str name="echoParams">explicit</str>
      <str name="tie">0.01</str>
      <str name="qf">
        content^0.5 anchor^1.0 title^1.2
      </str>
      <str name="pf">
        content^0.5 anchor^1.5 title^1.2 site^1.5
      </str>
      <str name="fl">
        url
      </str>
      <str name="mm">
        2&lt;-1 5&lt;-2 6&lt;90%
      </str>
      <str name="ps">100</str>
      <str name="hl">true</str>
      <str name="q.alt">*:*</str>
      <str name="hl.fl">title url content</str>
      <str name="f.title.hl.fragsize">0</str>
      <str name="f.title.hl.alternateField">title</str>
      <str name="f.url.hl.fragsize">0</str>
      <str name="f.url.hl.alternateField">url</str>
      <str name="f.content.hl.fragmenter">regex</str>
    </lst>
  </requestHandler>

```


Now, restart Tomcat:
```

# service tomcat6 restart

```

It is a good idea to tail -f the tomcat files and ensure that there are no errors.

[size="5"]Configuring Nutch[/size]
Go into the nutch directory and do all the work from there:
```

cd /usr/share/nutch

```

Edit conf/nutch-site.xml and add the following in between the <configuration>-clauses: 

```

  <property>
    <name>http.robots.agents</name>
    <value>nutch-solr-integration-test,*</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.name</name>
    <value>nutch-solr-integration-test</value>
    <description>FreeCode AS Robots Name</description>
  </property>
  <property>
    <name>http.agent.description</name>
    <value>FreeCode Norway Web Crawler using Nutch 1.0</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.url</name>
    <value>http://www.freecode.no/</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.email</name>
    <value>[COLOR="Red"]YOUR EMAIL ADDRESS HERE[/COLOR]</value>
    <description></description>
  </property>
  <property>
    <name>http.agent.version</name>
    <value></value>
    <description></description>
  </property>
  <property>
    <name>generate.max.per.host</name>
    <value>100</value>
  </property>

```

I need to ensure that the crawler does not leave our domain, otherwise I would end up crawling the entire Internet.

I inserted our domain into _conf/regex-urlfilter.txt:
```

# allow urls in freecode.no domain
+^[http://(](http://()[a-z0-9\-A-Z]*\.)*freecode.no/
 
# deny anything else
-.

```

Now, we need to instruct the crawler where to start crawling, so create a seed list:
```

# mkdir urls
# echo "http://www.freecode.no/" > urls/seed.txt

```

[size="5"]Crawling your site[/size]
Let's start crawling!

Start by injecting the seed url(s) to the nutch crawldb:
```

# bin/nutch inject crawl/crawldb urls

```

Next, generate fetch list:
```

# bin/nutch generate crawl/crawldb crawl/segments

```

The above command generated a new segment directory under /usr/share/nutch/crawl/segments that contains the urls to be fetched. All following commands require accessing the latest segment directory as their main parameter so we&#8217;ll store it in an environment variable:
```

export SEGMENT=crawl/segments/`ls -tr crawl/segments|tail -1`

```

Launch the crawler!
```

bin/nutch fetch $SEGMENT -noParsing

```

And parse the fetched content:
```

bin/nutch parse $SEGMENT

```

Now we need to update the crawl database to ensure that for all future crawls, Nutch only cheks the already crawled pages, and only fetches new and changed pages.
```

bin/nutch updatedb crawl/crawldb $SEGMENT -filter -normalize

```

Create a link database:
```

bin/nutch invertlinks crawl/linkdb -dir crawl/segments

```

Now a full Fetch cycle is completed. I have created a script to simplify the crawl job:
```

#!/bin/bash

# short script to help crawl

unset SEGMENT

# set this to your nutch home dir
NUTCH_HOME="/usr/share/nutch"

cd ${NUTCH_HOME}

${NUTCH_HOME}/bin/nutch generate crawl/crawldb crawl/segments
[ $? = 0 ] || { echo "An error occured while generating the fetch list!"; exit $?; }

export SEGMENT=crawl/segments/`ls -tr crawl/segments|tail -1`
${NUTCH_HOME}/bin/nutch fetch $SEGMENT -noParsing
[ $? = 0 ] || { echo "An error occured while FETCHING the content!"; exit $?; }

${NUTCH_HOME}/bin/nutch parse $SEGMENT
[ $? = 0 ] || { echo "An error occured while PARSING the content!"; exit $?; }

${NUTCH_HOME}/bin/nutch updatedb crawl/crawldb $SEGMENT -filter -normalize
[ $? = 0 ] || { echo "An error occured while updating the crawl DB!"; exit $?; }

${NUTCH_HOME}/bin/nutch invertlinks crawl/linkdb -dir crawl/segments
[ $? = 0 ] || { echo "An error occured while creating link database!"; exit $?; }

# success!
exit 0

#EOF

```

[size="5"]Indexing our crawl DB with solr[/size]
```

bin/nutch solrindex [http://127.0.0.1:8080/solr/](http://127.0.0.1:8080/solr/) crawl/crawldb crawl/linkdb crawl/segments/*

```

[size="5"]Search the crawled content in Solr[/size]
Now the indexed content is available through Solr. You can try to execute searches from the Solr admin ui from
```

[http://127.0.0.1:8080/solr/admin](http://127.0.0.1:8080/solr/admin)

```

or directly with url like:
```

[http://127.0.0.1:8080/solr/nutch/?q=kurs&amp;version=2.2&amp;start=0&amp;rows=10&amp;indent=on&amp;wt=json](http://127.0.0.1:8080/solr/nutch/?q=kurs&amp;version=2.2&amp;start=0&amp;rows=10&amp;indent=on&amp;wt=json)

```
Hi there - all goes well following your guide but I get stuck at bin/nutch inject crawl/crawldb urls
with the above error (32 bit ubuntu 10.10  nutch 1.2, tomcat6)

heres my .bashrc  - you can see I have tried several variables

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.22
export JAVA_OPTS="$JAVA_OPTS -Dsolr.solr.home=/var/lib/tomcat6/solr"
# If not running interactively, don't do anything
[ -z "$PS1" ] && return


and hadoop.env.sh

# Set Hadoop-specific environment variables here.

# The only required environment variable is JAVA_HOME.  All others are
# optional.  When running a distributed configuration it is best to
# set JAVA_HOME in this file, so that it is correctly defined on
# remote nodes.

# The java implementation to use.  Required.
# export JAVA_HOME=/usr/bin/java
#export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk
export JAVA_HOME=/usr/lib/jvm/java-6-sun
# The maximum amount of heap to use, in MB. Default is 1000.
# export HADOOP_HEAPSIZE=2000

# Extra Java runtime options.  Empty by default.
# export HADOOP_OPTS=-server

# Extra ssh options.  Default: '-o ConnectTimeout=1 -o SendEnv=HADOOP_CONF_DIR'.
# export HADOOP_SSH_OPTS="-o ConnectTimeout=1 -o SendEnv=HADOOP_CONF_DIR"

# Where log files are stored.  $HADOOP_HOME/logs by default.
# export HADOOP_LOG_DIR=${HADOOP_HOME}/logs

# File naming remote slave hosts.  $HADOOP_HOME/conf/slaves by default.
# export HADOOP_SLAVES=${HADOOP_HOME}/conf/slaves

# host:path where hadoop code should be rsync'd from.  Unset by default.
# export HADOOP_MASTER=master:/home/$USER/src/hadoop

# The directory where pid files are stored. /tmp by default.
# export HADOOP_PID_DIR=/var/hadoop/pids

# A string representing this instance of hadoop. $USER by default.
# export HADOOP_IDENT_STRING=$USER


hope you can help - thanks in advance

broomie

---

### Post by broomie on 2010-12-08
> **broomie said:**
> Hi there - all goes well following your guide but I get stuck at bin/nutch inject crawl/crawldb urls
with the above error (32 bit ubuntu 10.10  nutch 1.2, tomcat6)

heres my .bashrc  - you can see I have tried several variables

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.22
export JAVA_OPTS="$JAVA_OPTS -Dsolr.solr.home=/var/lib/tomcat6/solr"
# If not running interactively, don't do anything
[ -z "$PS1" ] && return


and hadoop.env.sh

# Set Hadoop-specific environment variables here.

# The only required environment variable is JAVA_HOME.  All others are
# optional.  When running a distributed configuration it is best to
# set JAVA_HOME in this file, so that it is correctly defined on
# remote nodes.

# The java implementation to use.  Required.
# export JAVA_HOME=/usr/bin/java
#export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk
export JAVA_HOME=/usr/lib/jvm/java-6-sun
# The maximum amount of heap to use, in MB. Default is 1000.
# export HADOOP_HEAPSIZE=2000

# Extra Java runtime options.  Empty by default.
# export HADOOP_OPTS=-server

# Extra ssh options.  Default: '-o ConnectTimeout=1 -o SendEnv=HADOOP_CONF_DIR'.
# export HADOOP_SSH_OPTS="-o ConnectTimeout=1 -o SendEnv=HADOOP_CONF_DIR"

# Where log files are stored.  $HADOOP_HOME/logs by default.
# export HADOOP_LOG_DIR=${HADOOP_HOME}/logs

# File naming remote slave hosts.  $HADOOP_HOME/conf/slaves by default.
# export HADOOP_SLAVES=${HADOOP_HOME}/conf/slaves

# host:path where hadoop code should be rsync'd from.  Unset by default.
# export HADOOP_MASTER=master:/home/$USER/src/hadoop

# The directory where pid files are stored. /tmp by default.
# export HADOOP_PID_DIR=/var/hadoop/pids

# A string representing this instance of hadoop. $USER by default.
# export HADOOP_IDENT_STRING=$USER


hope you can help - thanks in advance

broomie
SorryI missed the Title out - doh!    its kind of key:  Error: JAVA_HOME is not set.

---

### Post by habeeb5 on 2010-12-26
This tutorial rocks

---

### Post by habeeb5 on 2010-12-26
I folllowed the tutorial it is perfect running thank you.actually i want to crawl only arabic sites where to change the settings so that i can crawl arabic site only

thank you

---

### Post by gineta on 2010-12-26
uhmm it is really more difficult 
One because nutch can only crawl a designated list of domains or the whole Internet. 

But sure you can make a special crawl configuration for only accept arabic format.

I believe the best forum for make this question is in 
[http://lucene.472066.n3.nabble.com/Nutch-f603146.html](http://lucene.472066.n3.nabble.com/Nutch-f603146.html)

Please post here the solution if you get ;)
Thanks in advance

---

### Post by nxhoaf on 2011-03-09
Hi there, 
 I'm implementing module auto-form submission, which is one part of the project relating deep web crawler. The problem is, I must generate keyword to fill out the form. I wonder if Nutch store keywords (in some criteria) of these pages which it crawled somewhere ? if not, what can I do to obtain such data ?
Thanks.
ps: I'm new to Nutch.

---

### Post by guneza on 2011-03-14
> **nxhoaf said:**
> Hi there, 
 I'm implementing module auto-form submission, which is one part of the project relating deep web crawler. The problem is, I must generate keyword to fill out the form. I wonder if Nutch store keywords (in some criteria) of these pages which it crawled somewhere ? if not, what can I do to obtain such data ?
Thanks.
ps: I'm new to Nutch.

Sorry, that's more than my knowlege on Nutch.

---

