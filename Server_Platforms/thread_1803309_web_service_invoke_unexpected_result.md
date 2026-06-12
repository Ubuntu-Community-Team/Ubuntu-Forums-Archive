---
title: "web service invoke unexpected result"
date: 2011-07-13
forum: Server Platforms
---

### Post by manish.gupta@ionidea.com on 2011-07-13
Hi,
I am very new user for the web service .
In one portType 2 operations are defined. 
For each operation input message is blank massage type 
OutPut message is different for each.
when I invoke webservice each time first api is called. 
How can I resolve the same.
Any help will be appricated.
Configuration
 
<types>
<complexType name="ABC">
<sequence>
<element name="abc" type="string"/>
</sequence> 
</complexType>
<complexType name="DEF">
<sequence>
<element name="def" type="string"/>
</sequence> 
</complexType>
<element name="ABC" type="xsd1:ABC">
<element name="CDE" type="xsd1:ABC"> </types>
<message name="hcsDescription/"> 
<message name="ABCMSG">
<part name="body" element="xsd1:ABC"/>
</message>
<message name="DEFMSG">
<part name="body" element="xsd1:DEF"/>
</message>
<portType name="HCSStatus">
<operation nae="getFirst">
<input message="tns:hcsDescription"/>
<output message="tns:ABCMSG"/>
</operation>
<operation nae="getSecond">
<input message="tns:hcsDescription"/>
<output message="tns:DEFMSG"/>
</operation>
</portType>
<binding name="ABCStatusBinding" type="tns:ABCStatus">
<soap:binding style=""/>
<operation name="getFirst">
<soap:operation soapAction=""/>
<input>
<soap:body use="literal"/>
</input>
<output>
<soap:body use="literal"/>
</output>
</operation>
<operation name="getSecond">
<soap:operation soapAction=""/>
<input>
<soap:body use="literal"/>
</input>
<output>
<soap:body use="literal"/>
</output>
</operation>
</binding>
<service name="ABCStatus"> 
<port name="ABCStatusBinding" binding="tns:ABCStatusBinding">
<soap:address location="[http://localhost:8080/ProjectName/ABCStatus"/](http://localhost:8080/ProjectName/ABCStatus"/)>
</port>
</service>
</definitions>
Code is generated using apache cxf tool.
Service Invocation procedure is like this
 
JaxWsProxyFactoryBean factory = JaxWsProxyFactoryBean ();
factory.setServiceName(HCSSTatus.class);
factory.setAddress(Url);
hcsClint = factory.create();
Both call are returning the same output.
hcsClint.ABC();
hcsClint.DEF();
Please can you provide your any suggessation.

---

