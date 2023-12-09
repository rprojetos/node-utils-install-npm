# node-utils-install-nvm

Este documento trata da instalação e utilização do nvm.

## NVM

[Node Version Manager](https://github.com/nvm-sh/nvm), ou simplesmente NVM, é um gerenciador de versões do Node.js que permite a manutenção de múltiplas versões em um mesmo ambiente de desenvolvimente, ou seja, é um gerenciador especificamente de versões de Node.js.

## Instalando o NVM no Linux:

Sempre antes de instalar o nvm, verifica a versão mais atualizada em:

[Installing and Updating](https://github.com/nvm-sh/nvm#install--update-script)

1-Recomenda-se desinstalar o Node, antes da instalação do NVM, para não haver conflitos.

Comando para desinstalar o Node no Ubuntu:

```bash
sudo apt-get remove nodejs
```

2-Para instalar o NVM basta usar o curl ou Wget no terminal:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

ou

```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Será executado um script clonando o repositório NVM e jogando em um diretório ~/.nvm, onde serão instaladas as várias versões do Node.js que quisermos.

E então basta executar:

```bash
`source ~/.bash_profile`
```


# Comandos NVM

### Listar versões instaladas

Para ver as versões que estão instaladas em sua máquina:

```bash
nvm ls
```

### Listar versões disponíveis para instalação

Este comando lista todas as versões disponíveis para baixar e instalar na sua máquina. Esse número de versão será usado no comando para realizar a instalação.

```bash
nvm ls-remote
```

### Instalar uma versão

Para instalar usamos o comando `install` seguido pelo número da versão que queremos (mostrada no comando anterior, `ls-remote`).

Copiar

```bash
$ nvm install vX.X.X
```

Basta mudar os `X` pelos números da versão que quer baixar como `v.0.11.5` ou `v.12.4.0`.

Para instalar a versão mais recente, utilize `node` no lugar do número da versão:

Copiar

```bash
$ nvm install node
```

A primeira versão que você instalar será usada por padrão sempre que você abrir o terminal. A versão padrão pode ser alterada depois.

### Desinstalar uma versão

O comando `uninstall` é usado para desinstalar uma versão presente em nossa máquina. É utilizado da mesma maneira que o `install`

Copiar

```bash
$ nvm uninstall vX.X.X
```

### Usar uma versão do Node.js

Sempre que você abrir o terminal, a versão do Node.js usada é sempre a definida como padrão. Para usar outra versão instalada, execute o comando `use` seguido pela versão que você quer.

Copiar

```bash
$ nvm use vX.X.X
```

Para usar a versão mais recente, digite `node` no lugar da versão:

Copiar

```bash
$ nvm use node
```

Lembrando que ao abrir um novo terminal, a versão usada será novamente a definida como padrão.

### Definir nome para uma versão

Para não ter que ficar chamando uma versão pelo seu número, podemos definir um tipo de apelido para cada versão. Para isso usamos o comando `alias` e passamos o nome do apelido e a versão que queremos apelidar.

Copiar

```bash
$ nvm alias meunome vX.X.X
```

Com isso você poderá chamar a versão `vX.X.X` por `meunome`, como em:

Copiar

```bash
$ nvm use meunome
```

### Remover um nome de versão

Se você não quiser mais aquele apelido que você deu para uma versão, basta executar o comando `unalias` seguido pelo apelido que você quer esquecer.

Copiar

```bash
$ nvm unalias meunome
```

### Definir uma versão padrão

Para definir a versão que será usada sempre que você abrir o terminal, use o comando `alias` passando `default` como nome e em seguida a versão que você quer que seja a principal.

Copiar

```bash
$ nvm alias default vX.X.X
```

Para que a versão padrão seja a versão instalada mais recente, basta escrever `node` no lugar do número da versão:

Copiar

```bash
$ nvm alias default node
```

### Indicação da versão atual

Para saber qual a versão atual do Node.js o terminal está usando, basta executar o comando `current`.

Copiar

```bash
$ nvm current
```

### Migração de pacotes globais

Quando alteramos a versão do Node.js que está sendo utilizada, a versão do NPM muda junto. Isso significa que se você utiliza algum pacote do NPM globalmente em uma versão, não terá acesso a ele quando estiver usando outra versão.

Para não ter o trabalho de instalar cada pacote global a cada nova instalação do Node.js, basta adicionar `--reinstall-packages-from`.

Com esse comando podemos, por exemplo, instalar a versão 6 do Node.js e já mandar ele automaticamente instalar os pacotes globais do NPM que instalamos quando estávamos usando a versão 5.

Copiar

```bash
nvm install 6 --reinstall-packages-from=5
```

Como aprendemos até aqui, `node` é um atalho para indicar a versão mais recente. Caso queira instalar a versão mais recente disponível e já migrar os pacotes globais da versão mais recente que está instalada na sua máquina, basta executar:

Copiar

```bash
nvm install node --reinstall-packages-from=node
```

*No momento esta funcionalidade ainda não está disponível para o `nvm-windows`, sendo necessária a instalação manual dos pacotes globais sempre que instalar uma nova versão do Node.js.*

### Definição de versão por projeto

A intenção de usar o NVM é poder ter uma versão do Node.js para cada projeto, mas é muito difícil conseguir lembrar qual a versão foi usada em cada um.

Para isso, basta criar na raiz do projeto um arquivo com o nome `.nvmrc` e colocar dentro dele o número da versão do Node.js que está sendo utilizada nesse projeto, como:

Copiar

```
v12.4.0
```

Com isso, ao abrir o terminal dentro do projeto e executar o comando `nvm use`, o NVM vai automaticamente encontrar o arquivo `.nvmrc` e utilizar a versão indicada.

## Conclusão

Eu não costumava ligar para ter várias versões do Node.js em uma mesma máquina, pois sempre conseguia fazer funcionar em versões novas. Mas com o tempo pode acontecer de você ter que mexer em um código antigo e vai desperdiçar tempo arrumando para fazer funcionar caso esteja com uma versão nova.

Não só para linguagens de programação como Ruby e Python, mas outras ferramentas para desenvolvimento também como Unity, prefira sempre usar um gerenciador de versões, pois vai te economizar tempo e trabalho.
