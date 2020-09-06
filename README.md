# vim-configuration

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

After exploring multiple vim plugins and vim tips and tricks, I have finally managed to create and share unified vimrc configuration file.

Of course there is far too much to explore in vim so I will be updating this vimrc configuration continuously

### Installation

In order to set up your vim as python editor, you need to have python option enabled for vim.
for that you can hit following command

```sh
$ vim --version
```

the output will be something like following 

```
VIM - Vi IMproved 8.1 (2018 May 18, compiled Feb 14 2019 09:14:50)
Included patches: 1-918
Compiled by root@debian
Huge version without GUI.  Features included (+) or not (-):
+acl               +extra_search      +mouse_netterm     +tag_old_static
+arabic            +farsi             +mouse_sgr         -tag_any_white
+autocmd           +file_in_path      -mouse_sysmouse    -tcl
+autochdir         +find_in_path      +mouse_urxvt       +termguicolors
-autoservername    +float             +mouse_xterm       +terminal
-balloon_eval      +folding           +multi_byte        +terminfo
+balloon_eval_term -footer            +multi_lang        +termresponse
-browse            +fork()            -mzscheme          +textobjects
++builtin_terms    +gettext           +netbeans_intg     +textprop
+byte_offset       -hangul_input      +num64             +timers
+channel           +iconv             +packages          +title
+cindent           +insert_expand     +path_extra        -toolbar
-clientserver      +job               -perl              +user_commands
-clipboard         +jumplist          +persistent_undo   +vartabs
+cmdline_compl     +keymap            +postscript        +vertsplit
+cmdline_hist      +lambda            +printer           +virtualedit
+cmdline_info      +langmap           +profile           +visual
+comments          +libcall           +python            +visualextra
+conceal           +linebreak         -python3           +viminfo
+cryptv            +lispindent        +quickfix          +vreplace
+cscope            +listcmds          +reltime           +wildignore
+cursorbind        +localmap          +rightleft         +wildmenu
+cursorshape       -lua               -ruby              +windows
+dialog_con        +menu              +scrollbind        +writebackup
+diff              +mksession         +signs             -X11
+digraphs          +modify_fname      +smartindent       -xfontset
-dnd               +mouse             +startuptime       -xim
-ebcdic            -mouseshape        +statusline        -xpm
+emacs_tags        +mouse_dec         -sun_workshop      -xsmp
+eval              -mouse_gpm         +syntax            -xterm_clipboard
+ex_extra          -mouse_jsbterm     +tag_binary        -xterm_save
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
 2nd user vimrc file: "~/.vim/vimrc"
      user exrc file: "$HOME/.exrc"
       defaults file: "$VIMRUNTIME/defaults.vim"
  fall-back for $VIM: "/usr/share/vim"
```

notice +python present in the output.
If you dont have python enabled, no need to worry.
you can install vim-gtk package by using following command
```
$ sudo apt-get install vim-gtk
```
or can compile vim by yourself to enable python support using following commands
```
$ cd /tmp
$ git clone https://github.com/vim/vim.git
$ cd vim
$ ./configure --enable-pythoninterp --prefix=/usr
$ make 
$ sudo make install
```
once your vim has python option enabled, you can install following dependencies.
```
$ sudo apt-get install curl vim exuberant-ctags git ack-grep
$ sudo pip install pep8 flake8 pyflakes isort yapf
```
You can replace .vimrc file present with your own .vimrc file present in your home directory.

```sh
$ git clone https://github.com/rohan-97/vim-configuration.git
$ cd vim-configuration
$ cp -vp .vimrc $HOME/.vimrc
$ cd ..
```
once file is copied, you can open vim and run PluginInstall command
```
$ vim
$ :PluginInstall
```

### Plugins

Following is the list of plugins that I have used in my vimrc file.
You can refer following list and can suggest more.

| Plugin | README |
| ------ | ------ |
| Onedark Theme better look and feel | joshdick/onedark.vim |
| Code commenter | scrooloose/nerdcommenter |
| Code and files fuzzy finder | ctrlpvim/ctrlp.vim |
| Extension to ctrlp, for fuzzy command finder | fisadev/vim-ctrlp-cmdpalette |
| Zen coding | mattn/emmet-vim |
| Git integration | motemen/git-vim |
| Tab list panel | kien/tabman.vim |
| Airline | vim-airline/vim-airline |
| Airline Themes | vim-airline/vim-airline-themes |
| Surround | tpope/vim-surround |
| Autoclose | Townk/vim-autoclose |
| Indent text object | michaeljsmith/vim-indent-object |
| Better autocompletion | Shougo/neocomplcache.vim |
| Git/mercurial/others diff icons on the side of the file lines | mhinz/vim-signify |
| Python and other languages code checker | scrooloose/syntastic |

# Tmux Configuration

One change I have done for Tmux is that I have added branchname in right side of tmux status line.  
and changed default colour scheme of tmux status line.  
![status-bar](https://github.com/rohan-97/my-custom-configuraiton/blob/tmux-configuration/images/tmux-status-bar.PNG)

In order to identify the branch name I wrote a shell script `git-branch-name` which accepts directory path as command line parameter and prints the branch name if the directory comes under git repository ortherwise prints nothing

you can keep the `git-branch-name` script to any location, but if you add it to a location coming under PATH variable, then you can use git-branch-name as a command.

the tmux configuration file (~/.tmux.conf) is quiet simple and following are it's contents

```
set -g status-right-length 100
set -g status-style bg=default,fg=colour39
set -g status-right "#[fg=colour46,bg=default]#(git-branch-name #{pane_current_path}) #[fg=colour39,bg=default]#{=21:pane_title} %I:%M %p %d-%b-%y"
```

Note : I have added the script `git-branch-name` under `/usr/local/bin` directory so I am using git-branch-name as a command, if you are keeping the script under non-PATH directory, then kindly provide absolute path for git-branch-name in the tmux.conf

When you combine Tmux + Vim, you will get best development environment!

Following is the screenshot of my terminal showig a glimpse of tmux and vim in action.

![screenshot](https://github.com/rohan-97/my-custom-configuraiton/blob/tmux-configuration/images/Screenshot%20(88).png)


### Development

Want to contribute? Great!
please create your branches and raise pull requests.
I would be happy to hear about more awesome plugins
### Todos

 - Explore more plugins
 - Make vim one of the best editor ever

License
----

MIT


**Free Software, Hell Yeah!**
