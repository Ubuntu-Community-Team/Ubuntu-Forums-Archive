---
title: "axapta on ubuntu"
date: 2008-06-10
forum: Server Platforms
---

### Post by kalju24 on 2008-06-10
I hope i post this in the right forum 
Well my problem is quiet complicate 
i installed axapta on my pc that has ubuntu now i try to connect with my conf file so i could connect to s8ql and to thing like everybody else but e verytime i open i get an error and dosent log into axapta the error is :
An illegal directory structure for Axapta has been detected. The sub-directory smb://s8dsql/axapta$/\bin does not exist

i need to change my conf but what and how here is my conf

Configuration export file for Axapta

Formatversion: 1

Configuration: Client AXA_LIVE.axc

    language,Text,et

    directory,Text,smb://s8dsql/axapta$/

    company,Text,

    user,Text,

    client,Text,

    application,Text,standard

    broadcast,Text,

    internet,Text,S8DSQL

    aol,Text,sys

    aolcode,Text,

    sql,Int,1

    native,Int,0

    fetchahead,Text,

    opencursors,Text,

    database,Text,AXDB

    dsn,Text,

    sqluser,Text,bmssa

    hint,Text,

    sqlbuffer,Text,

    log,Text,

    hassqlpwd,Int,1

    sqlpwd,Text,!Ÿà¶Ý\l*

    sqlparm,Text,

    retry,Text,

    dbserver,Text,S8dSQL

    sqltrace,Text,0

    haswarnings,Int,0

    warnings,Text,

    bindir,Text,smb://s8dsql/axapta$/Bin

    startupmsg,Text,

    servermask,Text,Axapta

    localappldoc,Int,0

    localsysdoc,Int,0

    applshare,Int,1

    applexclusive,Int,0

    doclanguage,Text,

    startupcmd,Text,

    logdir,Text,

    hascompwd,Int,0

    compwd,Text,

    hasserveridletimeout,Int,0

    serveridletimeout,Text,

    connectionidletimeout,Text,

    querytimelimit,Text,

    extracmdline,Text,

    port,Text,

    createdsn,Text,

    aos,Text,

    allowunauth,Int,0

    exposeserverprinters,Int,0

    useserverprinters,Int,0

    sqlformliterals,Text,1

    sqlcomplexliterals,Text,1

    sqloraclefirstrowsfix,Text,0

    ignoredatasourceindex,Text,0

    aosencryption,Text,0

    xppdebug,Text,0

    dbcli,Text,odbc

    ociconnectservice,Text,1

    ociservice,Text,

    ocihost,Text,S8DSQL

    ocidbid,Text,AXDB

    ocitcpipport,Text,1521

    ociuser,Text,bmssa

    hasocipwd,Int,0

    ocipwd,Text,

    preloadthresholdmsec,Text,

    preloadthresholdrecords,Text,

    dbunicodeenabled,Text,0

    newconnectionretrydelayms,Text,

    newconnectionretrycount,Text,

    _clientmode,Int,0

    _clientadname,Text,

---

