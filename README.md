conf
====

some configuration files.such as svnignore/gitconfig and something else.


#执行下面的clone操作，~/.sys.bootstrap/zsh-config/.zshrc中会将该配置添加进来
git clone git@github.com:xiangguoqiang/.sys.config.git .sys.config


备注：
~/.sys.config/dirmark/zsh.sh 中包换了Tab键提示的逻辑。

主要是bindKey操作


_tab_complete_dirmark()
{
    case $BUFFER in
        "" )
            BUFFER="G "
            zle end-of-line
            _3tabs
            ;;
        "G"|"P"|"X")
            BUFFER="$BUFFER "
            zle end-of-line
            _3tabs
            ;;
        "G "|"P "|"X ")
            _3tabs
            ;;
        * )
            zle expand-or-complete
            ;;
    esac
}
zle -N _tab_complete_dirmark
bindkey "\t" _tab_complete_dirmark
