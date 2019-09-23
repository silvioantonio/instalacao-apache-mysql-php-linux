---
description: >-
  Passo a passo descontraido para instalação da stack LAMP - Apache, MySQL e PHP
  no Linux, de forma que possa ser instalado e utilizado por qualquer nivel de
  usuario.
---

# Como instalar Apache, MySQL e PHP no Ubuntu 14.04

## Sistema utilizado

Para efetuar a instalação e configuração das ferramentas descritas nesse tutorial, será utilizado a distribuição _Ubuntu_ versao 14.04 LTS do sistema **GNU/Linux**, em um ambiente virtual que esta utilizando 10Gb de HDD e 1Gb de memoria RAM, com um processador de 1 nucleos e 2 threads tendo 1.1 GHz em processamento, dessa forma sera possivel executar todas as instalações necessarias e tudo sem extressar o sistema.

## Preparando o sistema

Antes de começarmos a instalar as ferramentas necessarias para montarmos o ambiente LAMP, devemos preparar o nosso sistema para que não haja conflitos de versões ou quaisquer tipos de error durante as instalações.

### Removendo PHP, MySQL e APACHE

Geralmente em uma instalação recente de sistema, nao possuimos algumas funcionalidades, dessa forma fica muito facil instalar quaisquer coisas, porem, no caso contrario onde um usuario ja utilizava as ferramentas mas parou de utilizar, podemos ter certos conflitos com instalações ja presentes no sistema operacional.

por esse motivo, se faz necessario que antes de mais nada, seje feita uma limpeza no ambiente para evitar possiveis conflitos nas instalações.

#### Terminal Linux

Primeiro abra o terminal linux, e para isso existem varias formas, porem irei mostrar duas:

A primeira forma: `Ctrl + Alt + T` 

A segunda forma: Acesse os **Aplicativos** &gt; **Acessórios** e selecione **Terminal**


Existem outras formas de se abrir o terminal do linux, ou ate mesmo criar seu proprio atalho em qualquer lugar do sistema, recomendo fortemente que faça uma pesquisa sobre o assunto, alem de ser interessante, ainda é bem divertido poder manusear sua distribuição favorita da forma que quiser.


Dentro do terminal iremos utilizar alguns comandos, desse modo é necessario que voce possua o perfil de _super usuario_ ou tenha a senha do perfil _root_ para que possa usar os comando sem maiores problemas.

Habilitando terminal como usuario root:

```text
silvio@silvio:~$ sudo su
[sudo] senha para silvio: 
root@silvio:/home/silvio#
```

Habilitando terminal antes do comando como super usuario:

```text
silvio@silvio:~$ sudo <comando>
```

Os comandos seguintes irão remover todos os pacotes relacionados a versão que você tiver instalada em sua maquina.

#### PHP


Apenas lembre-se, caso nao esteja utilizando o perfil root dentro do terminal basta copiar e colar os comandos a seguir para executar as ações em sua distribuição, caso contrario, retire a palavra _`sudo`_ das linhas de comando e execute no terminal.



***Atenção

Estou removendo o php5 do meu sistema, caso você possua outra versao, basta mudar o numeral para que fique de acordo com a versão de sua utilização.


```
sudo apt-get remove --purge php5*
sudo apt-get autoremove
```

#### Apache

```text
sudo apt-get remove --purge apache*
sudo apt-get autoremove
```

#### MySQL

```text
sudo apt-get remove --purge mysql*
sudo apt-get autoremove
sudo rm -rf /var/lib/mysql
sudo rm -rf /etc/mysql
```

Pronto, dessa forma eliminamos quaisquer tipo de versões que poderial gerar conflitos com nossa instalação.

### Instalando o Aptitude

O **Aptitude** substitui o **apt-get** e ainda resolve as dependencias dos pacotes que estão sendo instalados. E para instalar o **Aptitude** é muito simples, iremos utilizar o **apt-get** para isso.

```text
sudo apt-get install aptitude
```

#### Atualizando repositórios

Precisamos de um repositorio novo para instalar o **PHP** atraves do aptitude, e para isso iremos utilizar o _python-software-properties_ que vai disponibilizar o comando `add-apt-repository` que nos permitira adicionar o repossitorio PPA\(Personal Package Archives\) de forma mais prática.

No terminal digite:

```text
sudo aptitude install python-software-properties software-properties-common
```

Agora atualize as listas de `apt` e `apt-get`

```text
sudo apt update
sudo apt-get update
```

## PHP + Apache + MySQL

Essa é uma stack muito conhecida no mundo do desenvolvimento, ou seja, possui um bom suporte e bons exemplos de aplicações praticas, entao sera mais facil utilizar as ferramentas e funcionalidades de cada item nesse conjunto.


#### Curiosidade

Essa mesma Stack\(LAMP\) pode ser utilizada em outro sistema operacional, porem ela muda de nome, no sistema Windows essa Stack se chama XAMP\(WAMP se preferir\).


### ATENÇÂO

durante toda a instalação você pode optar por utilzar os comandos de instalação padrões das ferramentas no terminal de qualquer distribuição linux. 

_Ao fim do tutorial irei colocar os comandos para se instalar as versões mais recentes da ferramenta sem muita complicação._


### PHP 5

Neste tutorial irei utilizar a versao 5 do PHP, caso voce queira utilizar outras versões, sugiro que leia a documentação oficial para melhores resultados.

[PHP - pagina oficial](https://www.php.net/)🚀

 É necessario que seja adicionado um novo PPA e atualizado a lista do apt-get.

```text
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo aptitude install php5 libapache2-mod-php5.1 php5.1-mysql php5.1-common php5.1-curl php5.1-json php5.1-xml php5.1-soap
```

### Apache 2

Novamente devo dizer que irei utilizar uma versao diferente a padrão, nesse caso a versao 5 do apache, como dito anteriormente, sera colocado ao fim do documento, os codigos para instalações genericas das versões atualizadas.

```text
sudo add-apt-repository ppa:ondrej/apache2
sudo apt-get update
sudo aptitude install apache2
```

[APACHE - pagina oficial ](http://httpd.apache.org/)🤖 

### MySQL

Durante a instalação do _MySQL_ sera solicitado uma senha para o banco MySQL, é extremamente recomendado que você coloque uma senha no campo e não deixe em branco.


#### Recomendação

Por padrão o usuario vem configurado como _root_ e pode ser modificado posteriormente, caso esqueça da senha ou usuario, bom, é melhor que anote para não esquecer!!!


```text
sudo aptitude install mysql-server
```

[MYSQL - pagina oficial](https://www.mysql.com/)🏦 

### Instalação simplificada

Como falado anteriormente, aqui estão os comandos para instalações simplificadas, da versão recente disponibilizada por cada site oficial.

#### Apache

primeiro atualize o gerenciador de pacotes

```text
sudo apt-get update -y
```

instalando o apache

```text
sudo apt-get install apache2 -y
```

#### MySQL

```text
sudo apt-get install mysql-server -y
```

Assim como da forma anterior de instalação do _mysql_, esse formata tambem ira solicitar uma senha para o usuario **root** do banco, novamente recomento fortemente que coloque e anote essa senha. E para qualquer outra pergunta durante a instalação digite "Y".

#### PHP

```text
sudo apt-get install php -y
sudo apt-get install libapache2-mod-php -y
```

{% hint style="info" %}
Essa instalação do PHP nao inclui outras bibliotecas que podem ser necessarias para a boa utilização do mesmo.

caso necessite de outras funcionalidades, sugiro verificar no site oficial junto a documentação.
{% endhint %}

## Autor

* [Linkedin](https://www.linkedin.com/in/silvio-antonio-de-oliveira-junior-621813142/)
* [Github](https://github.com/silvioantonio)
* [website](http://silvioantonio.ml/)

> Compartilhar conhecimento é a melhor forma de aprender
>
> -OLIVEIRA, Silvio Antonio Junior.

