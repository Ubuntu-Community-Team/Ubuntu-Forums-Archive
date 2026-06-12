---
title: "Error When Starting Audacity"
date: 2015-06-15
forum: Ubuntu Studio
---

### Post by G_M_Slater on 2015-06-15
When starting Audacity I get the following error. Has anyone encountered this before?

ASSERT INFO:
../src/common/menucmn.cpp(310): assert "wxIsStockID(GetId())" failed in SetItemLabel(): A non-stock menu item with an empty label?

BACKTRACE:
[1] wxMenuItemBase::SetItemLabel(wxString const&)
[2] wxMenuItemBase::wxMenuItemBase(wxMenu*, int, wxString const&, wxString const&, wxItemKind, wxMenu*)
[3] wxMenuItem::wxMenuItem(wxMenu*, int, wxString const&, wxString const&, wxItemKind, wxMenu*)
[4] wxMenuItemBase::New(wxMenu*, int, wxString const&, wxString const&, wxItemKind, wxMenu*)
[5] CommandManager::AddItem(wchar_t const*, wchar_t const*, CommandFunctor*, wchar_t const*, unsigned int, unsigned int, int)
[6] CommandManager::AddItem(wchar_t const*, wchar_t const*, CommandFunctor*, unsigned int, unsigned int)
[7] AudacityProject::AddEffectMenuItemGroup(CommandManager*, wxArrayString const&, wxArrayString const&, wxArrayInt const&, bool)
[8] AudacityProject::AddEffectMenuItems(CommandManager*, EffectPlugs&, int, int, bool)
[9] AudacityProject::PopulateEffectsMenu(CommandManager*, EffectType, int, int)
[10] AudacityProject::CreateMenusAndCommands()
[11] AudacityProject::AudacityProject(wxWindow*, int, wxPoint const&, wxSize const&)
[12] CreateNewAudacityProject()
[13] AudacityApp::FinishInits()
[14] wxEventLoopBase::SetActive(wxEventLoopBase*)
[15] wxEventLoopBase::Run()
[16] wxAppConsoleBase::MainLoop()
[17] wxAppConsoleBase::OnRun()
[18] wxAppBase::OnRun()
[19] wxEntry(int&, wchar_t**)
[20] wxEntry(int&, char**)
[21] main
[22] __libc_start_main
[23] _start

---

