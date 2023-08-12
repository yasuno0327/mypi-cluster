# ホームラボ用Ansible

## 概要
ホームラボで運用しているRaspberry Pi Clusterを管理するためのAnsibleです。
Ansibleでは各Raspberry Pi上で利用するzsh, gitなどのソフトウェアや, .zshrcなどの設定ファイルを管理します。

## Ansibleのインストール
pipを利用してインストールする
https://docs.ansible.com/ansible/2.9_ja/installation_guide/intro_installation.html#from-pip

```bash
pip install -r requirements.txt
```

ansibleのインストール先にpathを通す

```.zshrc
export PATH=$HOME/bin:/usr/local/bin:$HOME/.local/bin:$PATH
```

## hosts.ymlファイルの作成
hosts.yml.sampleの内容を参考にansible/hosts.ymlを作成してください

## 適用

```bash
cd ansible
ansible-playbook playbook.yml -i hosts.yml
# with debug log
# ansible-playbook -vvv playbook.yml -i hosts.yml
```

## 注意事項
playbook上の"Change theme to alanpeabody"タスクを反映させ、themeを変更するにはplaybook適用後に[Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)をインストールする必要があります。

インストールするには下記のコマンドを直接sshしてから叩いてください。(zshからinstall.shが叩かれることが想定されており、ansibleのshellプラグイン(shが使われる)などで上手く適用できないため、ここだけ手動にしています)
```bash

sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
