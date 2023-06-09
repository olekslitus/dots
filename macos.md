---
layout: post
title:  "How I setup my Mac"
date:   2021-05-12
categories: mac, setup
---

# Darwin
MacOS Big Sur 11.2.3 (20D91)

### System Preferences
1. Open `System Preferences`
2. Choose `General`
3. Uncheck `Allow wallpaper tinting in windows`
4. Uncheck `Close windows when quitting an app`
5. Uncheck `Allow Handoff between this Mac and your iCloud devices`
6. Return and choose `Dock & Menu Bar`
7. Uncheck `Animate opening applications`
8. Check `Automatically hide and show the Dock`
9. Uncheck `Show recent applications in Dock`

### Finder Preferences
1. Open `Preferences`
2. Uncheck all options for desktop
3. Set `New finder window show:` to your username
4. Choose `Sidebar`
5. Check home diretory
6. Uncheck tags
7. Uncheck hard drives
8. Uncheck Recent
9. 

### Create home directory
```
cd ~
mkdir Home
```

### Create dotfiles directory
```
cd ~/Home
mkdir dots
```

### Install Xcode (optional)
1. Open `App Store`
2. Log in with your Apple ID
3. Search `Xcode`
4. Click `Get`
5. Open `Xcode` and let it install components

### Install Bear Notes (optional)
1. Open `App Store`
2. Log in with your Apple ID
3. Search `Bear`
4. Click `Get`

### Install brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Install pictogram (optional)
```
brew install pictogram
```

### Install lunar (for external monitor)
```
brew install --cask lunar
```

### Install lightweight windows manager Rectangle
1. `brew install --cask rectangle`
2. Go to `Preferences`
3. Add 20 px gap

### Install nerd font (I like Fira Code, there are more)
```
brew tap homebrew/cask-fonts
brew install --cask font-fira-code-nerd-font
```

### Setup Terminal
```
1. Open Preferences
2. Choose `Profiles`
3. Press `Change...` next to Font
4. Choose installed nerd font, and size
```

### Setup ZSH (I also like fish)
1. `touch ~/Home/dots/zshrc`
2. `ln -s ~/Home/dots/zshrc ~/.zshrc`
3. Install Starship promt 
    - `brew install starship`
    - `eval "$(starship init zsh)"` add to the end of `~/.zshrc`
4. ...

### Install `exa` (todo: change this to isntall my toolkit)
```
brew install exa
# add `alias ls='exa -a --group-directories-first --git-ignore'` to ~/.zshrc
```

### Setup Ruby
```
brew install rbenv
rbenv init
# add to ~/.zshrc using vim/nano:
# eval "$(rbenv init -)"
exec "$SHELL"
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
rbenv install 3.0.0
rbenv global 3.0.0
```

### Setup Python
```
brew install pyenv
# add to ~/.zshrc using vim/nano:
# eval "$(pyenv init -)"
exec "$SHELL"
pyenv install 3.9.1
pyenv global 3.9.1
pyenv rehash
```

### Setup Rust
```
brew install rust
```

### Setup Racket
```
brew install racket
```

### Install VS Code (optional)
```
brew install visual-studio-code
mv ~/.vscode ~/Home/dots/vscode
ln -s ~/Home/dots/vscode ~/.vscode
```
Use pictogram to set icon from this directory. (optional)

### Setup VS Code
1. Open `Settings`
2. Set `workbench.settings.editor` to json
3. Open `Settings` again
4. Set `telemetry.enableTelemetry` to false



# o1-Mac Guide

## Initial Setup
### Settings
After full mac restart, or with a new mac first things to consider are it's basic settings.

#### Keyboard (Keychron K1)
1. Connect your keyboard at _System Preferences -> Bluetooth_
2. Add additional input sources at _System Preferences -> Keyboard -> Input Sources_
3. Map 'caps lock' to 'escape' on both keyboards at _System Preferences -> Keyboard -> Modifier Keys_
4. Press fn+S+O (for 3 seconds) to disable the Auto Sleep Mode.

#### Mouse (MX Master 2)
1. Download and install [Logitech Options](https://www.logitech.com/en-us/product/options).
2. Provide necessary permistion to Logitech Options at _System Preferences -> Security & Privacy -> Accessibility_
3. Log in into your Logitech Account.
4. Connect your mouse at _System Preferences -> Bluetooth_
5. You might need to reinstall 'Logitech Options' for it to pick up the mouth.
6. Map 'Middle Button' to 'Gecture'.
7. Map 'Thumb Button' to 'Launchpad'.
8. Adjust pointer speed to 3/5 using slider.

#### Display (Phylips 276E)
1. Go to _System Preferences -> Displays_
2. Connect display with wire.
3. Change display scale to 2560x1440.
4. Turn nightshift on from 'sunset to sunrise'.
5. Turn off 'Show mirroring options in the menu bar'.

#### General
1. Go to _System Preferences -> General_
2. Change apperenace to 'Dark'.
3. Switch scroll bar to 'When scrolling'.
4. Turn off Handoff.
5. Uncheck 'Close window when quiting an app'

#### Dock
1. Move to left.
2. Turn off 'Show recent applications in Dock'

#### Additional
1. Go to _System Preferences -> Apple ID -> iCloud -> iCloud Drive Options_
2. Check syns for Desktop and Documents folder.
3. Rename local name at _System Preferences -> Sharing_
4. Turn off 'Auto rearange Spaces' at _System Preferences -> Mission Control_
4. Turn on FileVault at 'Auto rearange Spaces' at _System Preferences -> Security & Privacy_

### Finder
1. Go to _Finder -> Prefrences... -> Sidebar_
2. Check your user directory
3. Check your mac directory
4. Uncheck Recents
5. Uncheck Recent Tags

### Safari
1. Go to _Safari -> Prefrences... -> General_
2. Change 'Safari opens with' to 'All windows from last session'
3. Change homepage appropriatyr
4. Uncheck 'Open "safe" files after downloading'

### Install Basics from App Store
- [Spark - best email for Mac](https://apps.apple.com/us/app/spark-email-app-by-readdle/id1176895641?mt=12)
- [Bear - great note taking app](https://apps.apple.com/us/app/bear/id1091189122?mt=12)

<br />

## Development Setup

### Directories
#### Home directory
1. Create directory ``$ mkdir /Users/user-name/Documents/Dev``
2. Create symbolic link ``$ ln -s /Users/user-name/Documents/Dev /Users/user-name/home``

#### Dotfiles control
Create directory ``$ mkdir ~/home/dotfiles``. 
All of the dotfiles are going to be stored in this directory and have symbolic links.

### Install
#### Xcode
1. Download and install [Xcode from App Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12).
2. Turn on Xcode and let it install all components.
3. Update system at _System Preferences -> Software Update_

#### Brew
1. Install [Brew](https://brew.sh/).
2. Run ``$ brew update``
3. Run ``$ brew upgrade``
4. Run ``$ brew doctor``

#### Install using brew
1. [iTerm](https://iterm2.com) ``$ brew install iterm``
2. [Fish](https://fishshell.com) ``$ brew install fish``
3. [Starship](https://starship.rs) ``$ brew install starship``
4. [exa](https://the.exa.website) ``$ brew install exa``
5. [wget](https://www.gnu.org/software/wget/) ``$ brew install wget``
6. [zzz](https://www.gnu.org/software/wget/) ``$ brew install zzz``
7. [Emacs](https://www.gnu.org/software/emacs/) ``$ brew cask install emacs``
8. [MacVim](https://macvim-dev.github.io/macvim/) ``$ brew cask install macvim``
9. [Racket](https://racket-lang.org) ``$ brew cask install racket``
10. [Firefox](https://www.mozilla.org/en-US/firefox/) ``$ brew cask install firefox``
11. [Typora](Typora) ``$ brew cask install typora``
12. [Telegram](https://telegram.org) ``$ brew cask install telegram``
13. [Slack](https://slack.com) ``$ brew cask install slack``
14. [Sublime](https://www.sublimetext.com) ``$ brew cask install sublime-text``

#### Install manually from sources
1. [Fira Code Font](https://github.com/tonsky/FiraCode)
2. [Java](https://java.com/en/download/)

#### Aditional intalls with seperate instuctions
1. [Doom Emacs](https://github.com/hlissner/doom-emacs)
``> git clone https://github.com/hlissner/doom-emacs ~/.emacs.d``
``> ~/.emacs.d/bin/doom install``


### Setup
#### Aliases
``$ alias -s del='rm -rf'``
``$ alias -s la='ls -a'``
``$ alias ls=exa``

#### Emacs
``> alias ec='emacs -nw' ``, where `-nw` stands for no window

#### Java
2. Uncheck Java from the Settings at ``System Preferences -> View -> Customize...``


#### Shell Setup - [Fish](https://fishshell.com)
2. Add fish to standart shells ``$ echo /usr/local/bin/fish | sudo tee -a /etc/shells``
3. Make fish default shell ``$ chsh -s `which fish` ``

5. Add starship to fish ``$ echo starship init fish | source >> ~/.config/fish/config.fish``

7. Run ``fish_config`` to configure fish

7.1. Go to ``iTerm -> Preferences -> Profiles -> Text``
7.2. Choose 'Underline' for cursor, and check 'blinking'
7.2. Check ``Use built-in Powerline glyphs``
7.3. Check ``Use a different font for non-ASCII text``
7.4. Choose Font to be Fira Code Retina 14 pt
7.5. Choose Non-ASCII Font to be Fira Code Retina 14 pt

8.1. Go to ``iTerm -> Preferences -> Profiles -> Window``
8.2. Change number of columns to be 90.
8.3. Change number of rows to be 30.

9.1. Go to ``iTerm -> Preferences -> Appearance -> General``
9.2. Change Theme to 'Minimal'

10.1. Go to ``iTerm -> Preferences -> Appearance -> Dimming``
10.2. Change amount to minimum

11.1. Go to ``iTerm -> Preferences -> General -> Closing``
11.2. Check 'Quit when all windows are closed'

12.1. Go to ``iTerm -> Preferences -> General -> Prefrences``
12.2. Activate 'load preferences from cutum folder', choose ``~/home/dotfiles``
12.3. Click 'Save current settings to folder'.
Note: my settings are available in dotfiles on github



```
function add-PATH
      set -U fish_user_paths $argv $fish_user_paths
end
funcsave add-PATH
```


---
layout: post
title:  "Mac ricing"
date:   2021-03-08
categories: mac, ricing
---

# mac-ricing
Guide to MacOS personalization (ricing) and collection of useful tools

#### What is ricing?

#### Community
reddit [r/unixporn](https://www.reddit.com/r/unixporn/)

## Guide

## Tools

### Text Editor
- VS Code
- Sublime

### Other
- http://www.hammerspoon.org/go/
- https://github.com/tmandry/whammy
- Karabiner
- bettertouchtool

### Shells
#### zsh
oh-my-zsh

#### fish
oh-my-fish

### WM - Windows Manager
#### yabai
[github]()

#### amethyst [github](https://github.com/ianyh/Amethyst) | [web](https://ianyh.com/amethyst/)

#### phoenix
[github](https://github.com/kasper/phoenix)

### Widget Contoller
#### uebersicht
[web](http://tracesof.net/uebersicht/)
[github](https://github.com/felixhageloh/uebersicht)
[support](https://bunq.me/fhageloh)
[github sponsor](https://github.com/sponsors/felixhageloh)

##### Bars
- https://github.com/kkga/nibar
- https://github.com/blaadje/fancyBar#readme
- https://github.com/AdamWagner/yabai-uberbar
- https://github.com/herrbischoff/nerdbar.widget

##### Other Widgets
- https://github.com/aCluelessDanny/UeberPlayer

### Launcher
-Finder (included with OS)
SpotLight (inclided with OS)
#### Alfred ...?

### Music Player
#### https://rybczak.net/ncmpcpp/

### Fonts
Nerd Fonts

### Doc
--??


## Cool Rices

#### Other dots
- https://github.com/atidyshirt/MacOS-Dotfiles/blob/master/.yabairc
- https://github.com/zzzeyez/dots/tree/master/yabai
- https://git.arul.io/arul/dotfiles/src/branch/macOS/zsh/.config/zsh/variables.zsh
- https://github.com/matchai/dotfiles/tree/b6c6a701d0af8d145a8370288c00bb9f0648b5c2/.config/fish

#### Awasome
- [PINK](https://www.reddit.com/r/unixporn/comments/kssnqs/yabai_pink/) 
by [OxidizedPixel](https://www.reddit.com/user/OxidizedPixel/)
| [dots](https://github.com/Who23/dots) 
| [wall](https://wallhaven.cc/w/5we787)
- [fun-colorful-rice](https://www.reddit.com/r/unixporn/comments/jupmda/aquayabai_a_fun_colorful_rice_to_brighten_my/)
by [Welcome_To_heaven](https://www.reddit.com/user/Welcome_To_heaven/)
| [dots](https://github.com/Welcome2Heaven/fun-colorful-rice)
- [Draconic Midnight](https://www.reddit.com/r/unixporn/comments/k4p0zy/yabaiaqua_draconic_midnight_aka_nighttime_rice_to/)
- [Amethyst/Aqua](https://www.reddit.com/r/unixporn/comments/jbmyc5/amethystaqua_macos_nord_more_gifs_in_comments/) | [dots](https://github.com/MCotocel/Dotfiles)
- [JAMR](https://www.reddit.com/r/unixporn/comments/him3tr/yabai_just_another_macos_rice/)

#### Cool
- [AQUA](https://www.reddit.com/r/unixporn/comments/9toocm/aqua_design_mac_osx/) by [blaadje](https://www.reddit.com/user/blaadje/)
- [lighthouse_comfy_oceanic](https://www.reddit.com/r/unixporn/comments/japeha/aquayabai_lighthouse_comfy_oceanic/)
- [Blood Moon](https://www.reddit.com/r/unixporn/comments/i4h39n/aquayabai_blood_moon/)
- [Big Nord Energy](https://www.reddit.com/r/unixporn/comments/fn7228/yabai_big_nord_energy/)

#### Okey
- [Hot and Cold](https://www.reddit.com/r/unixporn/comments/hpk32m/yabai_macos_big_sur_hot_and_cold/) | [dots](https://github.com/Nobody912/dotfiles)
- https://www.reddit.com/r/unixporn/comments/5xnd1k/macos_my_first_macos_ricing/
- https://www.reddit.com/r/unixporn/comments/5zuvgk/osx_macos_first_ricing_attempt_on_macos/
- https://www.reddit.com/r/unixporn/comments/55l19h/os_x_red_theme/
- https://www.reddit.com/r/unixporn/comments/ga7762/yabai_my_first_try_with_macos_ricing/

#### Found on imgur [link](https://imgur.com/a/1A6mW#aBsj7B3)
#### Found on medium [link](https://medium.com/@adrian.j.chen/mac-ricing-b763ac5de1b6)

## More resources
- https://sites.google.com/site/lazyboxx/desktops/ricing-openbox
- https://github.com/fosslife/awesome-ricing
- https://wiki.installgentoo.com/wiki/List_of_recommended_OS_X_software
- https://github.com/atsepkov/awesome-awesome-wm
- https://github.com/k4m4/terminals-are-sexy

- https://github.com/iCHAIT/awesome-macOS#readme
- https://github.com/herrbischoff/awesome-macos-command-line#readme
- https://github.com/agarrharr/awesome-macos-screensavers#readme
- https://github.com/jaywcjlove/awesome-mac#readme
- https://github.com/serhii-londar/open-source-mac-os-apps#readme


### Icons
- https://github.com/elrumo/macOS_Big_Sur_icons_replacements

## To Read
- https://rizonrice.github.io/resources
- https://www.mattgibson.ca/howto-ricing-mac-os-x-zsh-iterm2-borderless-padding-tmux-kwm/

