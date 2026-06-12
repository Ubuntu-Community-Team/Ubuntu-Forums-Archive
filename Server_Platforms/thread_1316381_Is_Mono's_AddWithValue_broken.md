---
title: "Is Mono's AddWithValue broken?"
date: 2009-11-05
forum: Server Platforms
---

### Post by paul_a_bennett on 2009-11-05
Is database inserting broken in mono?

I have been trying to do a database insert using mono's ASP.NET stuff for a while now.  It seems that if I use the suggested mechanisms, a new record is created in the database but no values are inserted into the fields.

For example, I have the following ASP.NET page that behaves this way:

<%@ Page Language="C#" Inherits="Sched2HT.Default" trace="true" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
	<title><asp:Literal id="SchedulePageTitle" Runat="Server" /></title>
</head>
<body>
	<form id="form1" runat="server">
          <asp:Literal
               id="CourseSelectionInstructions" 
               runat="server"
          />
          <br />
          <asp:ValidationSummary
               id="PageValidation"
               ShowMessageBox="true"
               ShowSummary="false"
               runat="server"
          />
          <br />
          <asp:ListBox
               id="CourseListBox"
               DatasourceID="CourseSource"
               DataTextField="CourseOffering"
               DataValueField="id"   
               Rows="12"
               runat="server"
          />
          <asp:RequiredFieldValidator
               id="RequiredCourse"
               ControlToValidate="CourseListBox"
               Font-Bold="true"
               Display="Dynamic"
               Text="(Required)"
               ErrorMessage="Course selection is required."
               runat="server"
          />
	      <asp:FormView
               id="ParticipantDetails"
               DataKeyNames="id"
               AllowPaging="false"
               DataSourceID="AttendeeSource"
               DefaultMode="Insert"
               runat="server"
               >
               <InsertItemTemplate>
                  <asp:Label
                       id="FirstNameLabel"
                       Text="First Name:"
                       AssociatedControlID="FirstNameTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="FirstNameTextBox"
                       Text='<%# Bind("FirstName") %>'
                       runat="server"
                  />
                  <br />
                  <br />
                  <asp:Label
                       id="LastNameLabel"
                       Text="Last Name:"
                       AssociatedControlID="LastNameTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="LastNameTextBox"
                       Text='<%# Bind("LastName") %>'
                       runat="server"
                  />
                  <br />
                  <br />
                  <asp:Label
                       id="EMailLabel"
                       Text="E-Mail Address:"
                       AssociatedControlID="EMailTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="EMailTextBox"
                       Text='<%# Bind("Email") %>'
                       runat="server"
                  />
                  <br />
                  <br />
                  <asp:Label
                       id="PhoneLabel"
                       Text="Telephone Number:"
                       AssociatedControlID="PhoneTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="PhoneTextBox"
                       Text='<%# Bind("Phone") %>'
                       runat="server"
                  />
                  <br />
                  <br />
               <asp:LinkButton
                    id="RegisterButton"
                    Text="Register"
                    CommandName="Insert"
                    runat="server"
               />
               </InsertItemTemplate>
          </asp:FormView>
          <asp:Literal
               id="TimeAndPlaceSelectionInstructions"
               runat="server"
          />
          <asp:SqlDataSource
               id="CourseSource"
               SelectCommand="select id, CourseOffering from Offerings"
               ConnectionString="<%$ ConnectionStrings:TwoHT %>"
               ProviderName="System.Data.Odbc"
               Runat="server"
          />
          <asp:SqlDataSource
               id="AttendeeSource"
               InsertCommand="insert into Attendees (FirstName, LastName, EMail, Phone) values (@FirstName, @LastName, @EMail, @Phone)"
               ConnectionString="<%$ ConnectionStrings:TwoHT %>"
               ProviderName="System.Data.Odbc"
               Runat="server"               
          />
	</form>
</body>
</html>

I've tried stripping things down to their essentials.  I created the following program which displays the same type of behaviour:

using System;
using System.Data;
using System.Data.Odbc;


namespace ODBCWriteTest
{
	class MainClass
	{
		public static void Main(string[] args)
		{
            OdbcConnection DbConnection = new OdbcConnection ("DSN=MySQLviaODBC;pwd=2HT");
            try
            {

    
                OdbcCommand DbCommand = DbConnection.CreateCommand ();
                DbCommand.CommandText = "Insert into Attendees (ScheduleID, FirstName, LastName, EMail, Phone) values (@ScheduleID, @FirstName, @LastName, @EMail, @Phone)";
                DbCommand.CommandType = CommandType.Text;
    
                DbCommand.Parameters.AddWithValue ("@ScheduleID", "999");
                DbCommand.Parameters.AddWithValue ("@FirstName", "First");
                DbCommand.Parameters.AddWithValue ("@LastName", "Last");
                DbCommand.Parameters.AddWithValue ("@EMail", "D@e.com");
                DbCommand.Parameters.AddWithValue ("@Phone", "123-678-1234");
                DbConnection.Open ();
                DbCommand.ExecuteNonQuery ();
            }
            finally
            {
                DbConnection.Close ();
            }                                      

		}
	}
}


Again, this inserts a record but no field data.

Before someone objects to my use of the ODBC instead of the MySQL adapter directly, that's because I couldn't get the MySQL adapter to work but I could get the ODBC adapter to work (as far as it does).

Now, here's the curious thing.

If, instead of using something like:

DbCommand.Parameters.AddWithValue ("@ScheduleID", "999");

I create an insert command using string concatenation, everything seems to work fine.  Documentation enjoins one from using this approach for security reasons, however.

I am left to wonder if AddWithValue is broken.

I would appreciate your input.

---

### Post by Vegan on 2009-11-05
As for as I can see you code is a bit ahead of where the mono-project is at right now.

You should ODBC for the database as direct access does not work at all in anything I have ever used even with Windows Server.

This is because there are so many databases competing for attention.

---

### Post by directhex on 2009-11-06
It possibly IS broken - if memory serves, Mono's ODBC implementation is layered on top of a library called GDA (GNOME Data Access), but a really really obsolete version of it

Which release are you trying to use? I know the MySQL Connector/NET was broken in one of them, but recent versions ought to behave

---

### Post by paul_a_bennett on 2009-11-06
I'm using the following versions:

$ monodevelop -V
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
MonoDevelop Ide  2.0.0.0 - GPL
The MonoDevelop IDE application.



And 

$ mono -V
Mono JIT compiler version 2.4.2.3 (Debian 2.4.2.3+dfsg-2)
Copyright (C) 2002-2008 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none

---

### Post by directhex on 2009-11-06
Using Connector/NET directly should be fine on Karmic. Intrepid it was broken.

The following VB.NET code:
```
Imports System
Imports System.Data
Imports MySql.Data.MySqlClient


Module MySqlConnect

   Sub Main()
      Dim connString As String = "Database=Test;Data Source=localhost;User Id=root;Password="

      Dim conn As New MySqlConnection(connString)

      Try
         conn.Open()
         Console.WriteLine("Connection Opened")

         Console.WriteLine("Connection Properties")
         Console.WriteLine("- ConnectionString : {0}", conn.ConnectionString)
         Console.WriteLine("- Database : {0}", conn.Database)
         Console.WriteLine("- DataSource : {0}", conn.DataSource)
         Console.WriteLine("- ServerVersion : {0}", conn.ServerVersion)
         Console.WriteLine("- State : {0}", conn.State)

      Catch ex As MySqlException
         ' Display error
         Console.WriteLine("Error: " & ex.ToString())
      Finally
         ' Close Connection
         conn.Close()
         Console.WriteLine("Connection Closed")

      End Try
   End Sub
End Module
```

works fine & yields:
```
Connection Opened
Connection Properties
- ConnectionString : database=Test;data source=localhost;user id=root
- Database : Test
- DataSource : localhost
- ServerVersion : 5.1.37-1ubuntu5
- State : Open
Connection Closed
```

so I'm not 100% sure why you say Connector/NET doesn't work. If there's definitely a bug with Mono's ODBC support, then feel free to file a bug upstream on bugzilla.novell.com

---

### Post by paul_a_bennett on 2009-11-06
Thanks for your note.

I notice from your code that you never actually write to the database.

None of my code has any problem opening the database connection or selecting from it.

The issue only arises when I try to do an insert. (I've not tried updates, yet).

Have you tried doing inserts with the MySQL connector?

---

### Post by paul_a_bennett on 2009-11-06
Thanks.  Your suggestions have been helpful.

I managed to get the following code to work correctly:

using System;
using System.Data;
using MySql.Data;
using MySql.Data.MySqlClient;



namespace MySQLWriteTest
{
	class MainClass
	{
        private static MySqlParameter CreateParameter (string parameterName, string parameterValue)
        {
            MySqlParameter newParameter = new MySqlParameter ();
            newParameter.ParameterName  = parameterName;
            newParameter.Value          = parameterValue;
            return newParameter;
        }
        
		public static void Main(string[] args)
		{
			string ConnectionString = "Database=secret;Server=secret;User ID=secret;Password=secret;";
            string insertCommand = "insert into Attendees (ScheduleID, FirstName, LastName, EMail, Phone) values (@ScheduleID, @FirstName, @LastName, @EMail,
 @Phone)";
		    MySqlConnection connection = new MySqlConnection (ConnectionString);
            try 
            {
                connection.Open ();
               
                MySqlCommand command = new MySqlCommand (insertCommand, connection);

                MySqlParameter ScheduleIDParameter = CreateParameter ("@ScheduleID", "999");
                MySqlParameter FirstNameParameter  = CreateParameter ("@FirstName",  "First");
                MySqlParameter LastNameParameter   = CreateParameter ("@LastName",   "Last");
                MySqlParameter EMailParameter      = CreateParameter ("@EMail",      "D@e.com");
                MySqlParameter PhoneParameter      = CreateParameter ("@Phone",      "123-456-7890");
                command.Parameters.Add (ScheduleIDParameter);
                command.Parameters.Add (FirstNameParameter);
                command.Parameters.Add (LastNameParameter);
                command.Parameters.Add (EMailParameter);
                command.Parameters.Add (PhoneParameter);
  
                command.ExecuteNonQuery ();
                
                connection.Close ();
            }
            catch (Exception e)
            {
                Console.WriteLine (e.ToString ());
            }
            
            

            
		}
	}
}

Now, my question is, going back to my original ASPX page, how do I set the ProviderName correctly in order to use the MySQL connector?

I've tried using the following:

<%@ Page Language="C#" Inherits="Sched2HT.Default" trace="true" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
	<title><asp:Literal id="SchedulePageTitle" Runat="Server" /></title>
</head>
<body>
	<form id="form1" runat="server">
          <asp:Literal
               id="CourseSelectionInstructions" 
               runat="server"
          />
          <br />
          <asp:ValidationSummary
               id="PageValidation"
               ShowMessageBox="true"
               ShowSummary="false"
               runat="server"
          />
          <br />
          <asp:ListBox
               id="CourseListBox"
               DatasourceID="CourseSource"
               DataTextField="CourseOffering"
               DataValueField="id"   
               Rows="12"
               runat="server"
          />
          <asp:RequiredFieldValidator
               id="RequiredCourse"
               ControlToValidate="CourseListBox"
               Font-Bold="true"
               Display="Dynamic"
               Text="(Required)"
               ErrorMessage="Course selection is required."
               runat="server"
          />
	      <asp:FormView
               id="ParticipantDetails"
               DataKeyNames="id"
               AllowPaging="false"
               DataSourceID="AttendeeSource"
               DefaultMode="Insert"
               runat="server"
               >
               <InsertItemTemplate>
                  <asp:Label
                       id="FirstNameLabel"
                       Text="First Name:"
                       AssociatedControlID="FirstNameTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="FirstNameTextBox"
                       Text='<%# Bind("FirstName") %>'
                       runat="server"
                  />
                  <br />
                  <br />
                  <asp:Label
                       id="LastNameLabel"
                       Text="Last Name:"
                       AssociatedControlID="LastNameTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="LastNameTextBox"
                       Text='<%# Bind("LastName") %>'
                       runat="server"
                  />
                  <br />
                  <br />
                  <asp:Label
                       id="EMailLabel"
                       Text="E-Mail Address:"
                       AssociatedControlID="EMailTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="EMailTextBox"
                       Text='<%# Bind("Email") %>'
                       runat="server"
                  />
                  <br />
                  <br />
                  <asp:Label
                       id="PhoneLabel"
                       Text="Telephone Number:"
                       AssociatedControlID="PhoneTextBox"
                       runat="server"
                  />
                  <asp:TextBox
                       id="PhoneTextBox"
                       Text='<%# Bind("Phone") %>'
                       runat="server"
                  />
                  <br />
                  <br />
               <asp:LinkButton
                    id="RegisterButton"
                    Text="Register"
                    CommandName="Insert"
                    runat="server"
               />
               </InsertItemTemplate>
          </asp:FormView>
          <asp:Literal
               id="TimeAndPlaceSelectionInstructions"
               runat="server"
          />
          <asp:SqlDataSource
               id="CourseSource"
               SelectCommand="select id, CourseOffering from Offerings"
               ConnectionString="<%$ ConnectionStrings:TwoHT %>"
               ProviderName="MySql.Data.MySqlClient"
               Runat="server"
          />
          <asp:SqlDataSource
               id="AttendeeSource"
               InsertCommand="insert into Attendees (FirstName, LastName, EMail, Phone) values (@FirstName, @LastName, @EMail, @Phone)"
               ConnectionString="<%$ ConnectionStrings:TwoHT %>"
               ProviderName="MySql.Data.MySqlClient"
               Runat="server"               
          />
	</form>
</body>
</html>


When I do, I get the following:

Server Error in '/' Application
Failed to find or load the registered .Net Framework Data Provider 'MySql.Data.MySqlClient'.

Description: HTTP 500. Error processing request.

Stack Trace:

System.Configuration.ConfigurationErrorsException: Failed to find or load the registered .Net Framework Data Provider 'MySql.Data.MySqlClient'.
  at System.Data.Common.DbProviderFactories.GetFactory (System.String providerInvariantName) [0x00026] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Data/System.Data.Common/DbProviderFactories.cs:80 
  at System.Web.UI.WebControls.SqlDataSource.GetDbProviderFactory () [0x00012] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/SqlDataSource.cs:94 
  at System.Web.UI.WebControls.SqlDataSource.GetDbProviderFactoryInternal () [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/SqlDataSource.cs:103 
  at System.Web.UI.WebControls.SqlDataSourceView.InitConnection () [0x0000b] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/SqlDataSourceView.cs:58 
  at System.Web.UI.WebControls.SqlDataSourceView.ExecuteSelect (System.Web.UI.DataSourceSelectArguments arguments) [0x000a2] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/SqlDataSourceView.cs:206 
  at System.Web.UI.WebControls.ListControl.OnDataBinding (System.EventArgs e) [0x00007] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ListControl.cs:398 
  at System.Web.UI.WebControls.ListControl.PerformSelect () [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ListControl.cs:505 
  at System.Web.UI.WebControls.BaseDataBoundControl.DataBind () [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:143 
  at System.Web.UI.WebControls.BaseDataBoundControl.EnsureDataBound () [0x00016] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:149 
  at System.Web.UI.WebControls.BaseDataBoundControl.OnPreRender (System.EventArgs e) [0x00007] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/BaseDataBoundControl.cs:182 
  at System.Web.UI.WebControls.ListControl.OnPreRender (System.EventArgs e) [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ListControl.cs:411 
  at System.Web.UI.WebControls.ListBox.OnPreRender (System.EventArgs e) [0x00000] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI.WebControls/ListBox.cs:209 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x0003b] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:1536 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00072] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:1543 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00072] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Control.cs:1543 
  at System.Web.UI.Page.ProcessLoadComplete () [0x00089] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Page.cs:1647 
  at System.Web.UI.Page.InternalProcessRequest () [0x001cb] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Page.cs:1536 
  at System.Web.UI.Page.ProcessRequest (System.Web.HttpContext context) [0x0005b] in /build/buildd/mono-2.4.2.3+dfsg/mcs/class/System.Web/System.Web.UI/Page.cs:1353 

Version information: Mono Version: 2.0.50727.1433; ASP.NET Version: 2.0.50727.1433


Am I misconfiguring something?

---

### Post by paul_a_bennett on 2009-11-06
OK. Well, I got it going.

I simply added the following to my web.config file:

  <system.data>
    <DbProviderFactories>
        <clear />
        <add name="MySQL Data Provider"
             invariant="MySql.Data.MySqlClient"
             description=".Net Framework Data Provider for MySQL"
             type="MySql.Data.MySqlClient.MySqlClientFactory, MySql.Data, Version=5.2.1.0, Culture=neutral, PublicKeyToken=20449f9ba87f7ae2"
         />
        </DbProviderFactories>
  </system.data>

Thanks for your help.

All the best!

Paul

---

### Post by directhex on 2009-11-06
Glad you got it working. ASP.NET is still something of an unknown for me.

---

