---
title: "UNIX server with SQL Server 2005 support"
date: 2011-10-02
forum: Server Platforms
---

### Post by silverwolf5 on 2011-10-02
Hi all.
I'm about to start a company, but here in Portugal sales software must have a national certification to be legal, the one's I've found so far all of them only support SQL Server 2005/2008 or Access. Since there is none supporting Linux and MySQL and due to high costs of implementing Microsoft solutions I need a mid-term solution.

The sales software I have is Gespos Retail, from Sage. It supports only Windows and MS SQL Server 2005 / Access databases.

Is there a way to have a UNIX server to host both a website (which will query the SQL database locally) and a MS SQL Server 2005 database running 24/7?

I also intend to use xubuntu on low end machines to run Gespos through Wine, any recomendations on this? As anyone tried something similar?

Thanks.

---

### Post by volkswagner on 2011-10-02
Depending on your hardware, you may be able to run an MS Windows virtual machine inside a Linux host.  Or you can choose a bare metal hypervisor  and run Linux and MS Windows VM's.

Be sure to check out the capability and license agreement of [SQL Server Express]("http://www.microsoft.com/express") to see if you can use it a $free solution.

---

### Post by SeijiSensei on 2011-10-02
Wow, what a nice legal monopoly for Microsoft!  Any options that use PostgreSQL?  Oracle?  Both of these have native Linux implementations, though the latter will probably cost more than MS SQL.

Here are some options you might consider:

1)  Virtualization
Install Windows Server in a [VirtualBox]("http://www.virtualbox.org/") VM running within a Ubuntu host. Communicate with SQL Server using:

a) [UnixODBC]("http://www.unixodbc.org/")

b) PHP using the native [MS SQL]("http://php.net/manual/en/book.mssql.php") client or its UnixODBC client.

2)  Clients
Your Wine solution might work.  Does Gespos include a light-weight client that can communicate with the server over the network?  That might work better in a Wine environment.

---

### Post by silverwolf5 on 2011-10-02
I thought of that solution too, but I think it will create much overhead running a Windows OS in a VM to host a SQL database.

I also thought of creating a folder on the server with an Access database, no good solution too because of permissions and querys.

I wish to keep it rather simple and flexible (and cheap) for future modification/implementations. Since it is a cheap webserver with reasonable resources for a small starting bussiness, using an hypervisor I would end up buying Windows OS anyway for legal purpose.

Is there some kind of API to SQL Server 2005 like Wine?
Or a way to emulate/run as service a DBMS from Microsoft?

Thanks for your reply.

---

### Post by silverwolf5 on 2011-10-02
> **SeijiSensei said:**
> Wow, what a nice legal monopoly for Microsoft!  Any options that use PostgreSQL?  Oracle?  Both of these have native Linux implementations, though the latter will probably cost more than MS SQL.

Here are some options you might consider:

1)  Virtualization
Install Windows Server in a [VirtualBox]("http://www.virtualbox.org/") VM running within a Ubuntu host. Communicate with SQL Server using:

a) [UnixODBC]("http://www.unixodbc.org/")

b) PHP using the native [MS SQL]("http://php.net/manual/en/book.mssql.php") client or its UnixODBC client.

2)  Clients
Your Wine solution might work.  Does Gespos include a light-weight client that can communicate with the server over the network?  That might work better in a Wine environment.

Yeah, Microsoft basically owns the place. Open-source software is pretty much non existant only a pretty idea to some bussiness. Maybe that's why we are non-competitive and in a crysis? lol

Anyway here's the list of certificed software if you care to check: [http://www.portaldasfinancas.gov.pt/pt/consultaProgCertificadosM24.action](http://www.portaldasfinancas.gov.pt/pt/consultaProgCertificadosM24.action)

I've not searched for Oracle solutions though, my studies were only in Windows/SQL server and a bit of Linux. Since MySQL is rather similar I believe I can make something work out of it with low costs.

Yes. Gespos allows you to access through network or a remote SQL Server host.
Sage, Primavera and PHC are the most used in small bussiness in Portugal.

---

### Post by koenn on 2011-10-02
> **silverwolf5 said:**
> 
I'm about to start a company
...
a national certification to be legal, the one's I've found so far all of them only support SQL Server 2005/2008 or Access. 

So, you need to install a Windows server and a MS SQL 2005/2008 [Express], and include the costs in your business plan. Simple.

---

### Post by silverwolf5 on 2011-10-03
> **koenn said:**
> So, you need to install a Windows server and a MS SQL 2005/2008 [Express], and include the costs in your business plan. Simple.


That's the whole point for finding a possible free alternative.
I guess I'll stick with the Virtualbox and virtualize windows server.
Thanks anyway.

---

