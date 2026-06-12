---
title: "I get a lot of erros when i try to compile"
date: 2012-06-16
forum: Ubuntu Application Development
---

### Post by MaXwEllDeN on 2012-06-16
Hi Guys, i'm trying to learn more about wxWidgets, so i am trying to compile a example file but ever that i do it i get those errors:

```

maxwellden@MaXwEllDeN:~$ cd ~/wxStart
maxwellden@MaXwEllDeN:~/wxStart$ make
g++ `wx-config --cxxflags --libs` main.cpp -o wxTeste
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/cc5YeGY3.o: In function `wxTeste::OnInit()':
main.cpp:(.text+0x44): undefined reference to `Janelinha::Janelinha(wxString const&, int, int)'
/tmp/cc5YeGY3.o: In function `wxStringBase::wxStringBase(wchar_t const*)':
main.cpp:(.text._ZN12wxStringBaseC2EPKw[_ZN12wxStringBaseC5EPKw]+0x7): undefined reference to `wxStringBase::npos'
main.cpp:(.text._ZN12wxStringBaseC2EPKw[_ZN12wxStringBaseC5EPKw]+0x25): undefined reference to `wxStringBase::InitWith(wchar_t const*, unsigned int, unsigned int)'
/tmp/cc5YeGY3.o: In function `wxTransform2D::Transform(wxRect2DInt*) const':
main.cpp:(.text._ZNK13wxTransform2D9TransformEP11wxRect2DInt[wxTransform2D::Transform(wxRect2DInt*) const]+0x89): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
/tmp/cc5YeGY3.o: In function `wxTransform2D::InverseTransform(wxRect2DInt*) const':
main.cpp:(.text._ZNK13wxTransform2D16InverseTransformEP11wxRect2DInt[wxTransform2D::InverseTransform(wxRect2DInt*) const]+0x89): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x8): undefined reference to `wxApp::GetClassInfo() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x14): undefined reference to `wxObject::CreateRefData() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x18): undefined reference to `wxObject::CloneRefData(wxObjectRefData const*) const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x1c): undefined reference to `wxEvtHandler::ProcessEvent(wxEvent&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x20): undefined reference to `wxEvtHandler::SearchEventTable(wxEventTable&, wxEvent&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x28): undefined reference to `wxEvtHandler::TryParent(wxEvent&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x2c): undefined reference to `wxApp::GetEventTable() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x30): undefined reference to `wxApp::GetEventHashTable() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x34): undefined reference to `wxEvtHandler::DoSetClientObject(wxClientData*)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x38): undefined reference to `wxEvtHandler::DoGetClientObject() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x3c): undefined reference to `wxEvtHandler::DoSetClientData(void*)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x40): undefined reference to `wxEvtHandler::DoGetClientData() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x44): undefined reference to `wxApp::Initialize(int&, wchar_t**)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x50): undefined reference to `wxApp::OnInitGui()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x54): undefined reference to `wxAppBase::OnRun()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x58): undefined reference to `wxAppBase::OnExit()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x5c): undefined reference to `wxApp::CleanUp()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x64): undefined reference to `wxAppBase::Exit()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x68): undefined reference to `wxAppBase::OnInitCmdLine(wxCmdLineParser&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x6c): undefined reference to `wxAppBase::OnCmdLineParsed(wxCmdLineParser&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x70): undefined reference to `wxAppConsole::OnCmdLineHelp(wxCmdLineParser&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x74): undefined reference to `wxAppConsole::OnCmdLineError(wxCmdLineParser&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x78): undefined reference to `wxAppConsole::FilterEvent(wxEvent&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x7c): undefined reference to `wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x84): undefined reference to `wxAppConsole::ProcessPendingEvents()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x88): undefined reference to `wxApp::Yield(bool)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x8c): undefined reference to `wxApp::WakeUpIdle()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x90): undefined reference to `wxAppBase::CreateTraits()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x94): undefined reference to `wxAppBase::MainLoop()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x98): undefined reference to `wxAppBase::ExitMainLoop()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0x9c): undefined reference to `wxAppBase::Pending()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xa0): undefined reference to `wxAppBase::Dispatch()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xa4): undefined reference to `wxAppBase::ProcessIdle()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xa8): undefined reference to `wxAppBase::SendIdleEvents(wxWindow*, wxIdleEvent&)'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xac): undefined reference to `wxAppBase::OnExceptionInMainLoop()'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xb4): undefined reference to `wxAppBase::GetTopWindow() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xb8): undefined reference to `wxAppBase::GetDisplayMode() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xc4): undefined reference to `wxAppBase::GetLayoutDirection() const'
/tmp/cc5YeGY3.o:(.rodata._ZTV7wxTeste[vtable for wxTeste]+0xc8): undefined reference to `wxAppBase::SetActive(bool, wxWindow*)'
/tmp/cc5YeGY3.o: In function `wxTeste::~wxTeste()':
main.cpp:(.text._ZN7wxTesteD2Ev[_ZN7wxTesteD5Ev]+0x16): undefined reference to `wxApp::~wxApp()'
/tmp/cc5YeGY3.o:(.rodata._ZTV20wxThreadHelperThread[vtable for wxThreadHelperThread]+0xc): undefined reference to `wxThread::TestDestroy()'
/tmp/cc5YeGY3.o: In function `wxThreadHelperThread::~wxThreadHelperThread()':
main.cpp:(.text._ZN20wxThreadHelperThreadD2Ev[_ZN20wxThreadHelperThreadD5Ev]+0x16): undefined reference to `wxThread::~wxThread()'
/tmp/cc5YeGY3.o:(.rodata._ZTI7wxTeste[typeinfo for wxTeste]+0x8): undefined reference to `typeinfo for wxApp'
/tmp/cc5YeGY3.o:(.rodata._ZTI20wxThreadHelperThread[typeinfo for wxThreadHelperThread]+0x8): undefined reference to `typeinfo for wxThread'
collect2: ld returned 1 exit status
make: ** [all] Erro 1
maxwellden@MaXwEllDeN:~/wxStart$ 

```

There is the example project, it is the first:
[http://zetcode.com/tutorials/wxwidgetstutorial/firstprograms/](http://zetcode.com/tutorials/wxwidgetstutorial/firstprograms/)


*** Sorry for my bad English Z:

---

### Post by mhall119 on 2012-06-16
Maybe you need to install a dev package like libwxbase2.8-dev or wx2.8-headers?

---

### Post by MaXwEllDeN on 2012-06-16
I Already have it :(

---

### Post by mhall119 on 2012-06-16
Then you might want to try asking on [AskUbuntu]("http://www.askubuntu.com/questions/ask?tags=application-development"), or perhaps finding the wxWidgets community.

---

