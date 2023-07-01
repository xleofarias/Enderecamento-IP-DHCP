# Enderecamento-IP-DHCP

# Ferramenta Cisco Packet Tracer

Quem irá atuar como nosso servidor DHCP neste exemplo, será o roteador da Cisco. Ele fornecerá endereços IPs automaticamente para os computadores.

1. Passo - Criação dos dispositivos e conectando os dispositivos
   - Crie os computadores quantos desejar.
   - Crie um switch para conectar os computadores.
   - Agora é hora de conectar os computadores no switch utilizando o cabo direto(copper straight through cable) conectando em cada porta FastEthernet.
   - Depois crie um roteador e conecte ao switch usando o cabo direto em uma porta FastEthernet.
   - Direto da ferramenta podemos acessar o terminal do roteador para configurar a interface de rede, mas iremos utilizar como se fosse na vida real, conectando um computador por fora.
   - Crie um computador e conecte ele utilizando o cabo Console(O azul) no computador sera a porta RS 232 e no roteador na porta Console.

2. Passo - Configurando a interface de rede pelo terminal(CLI)
   - Acesse o terminal do computador conectado ao roteador.
   - Agora iremos utilizar o comando **"enable"** para ativar, digamos assim o modo administrador.
   - logo após isso iremos utilizar o comando **"configure terminal"**, assim estamos agora configurar o terminal.
   - Agora iremos habilitar as portas do roteador para o switch a FastEthernet.
   - Utilize o comando **"interface FastEthernet"** com a porta que o switch ta conectado no roteador, aqui é a 0/0.
   - Agora iremos habilitar essa porta com o comando **"no shutdown"**.
   - Use o **"exit"** ele irá retorna para configuração da interface do terminal. Agora iremos ativar o DHCP.
   - Para configurar o DHCP use o comando **"ip dhcp pool [nome do pool, pode se qualquer nome mas grave ele]"**.
   - Acessamos a configuração do DHCP e iremos criar uma default gateway para todos os computadores.
   - Utilize o comando **"default-router"** e crie um IP para ele. Esse IP será a porta gateway de todos os computadores, para acessar a internet.
   - Agora iremos criar a nossa rede, com o comando network, ainda dentro da configuração do DHCP. Crie um IP diferente da porta gateway.
   - Agora precisamos sair da configuração de rede e ir para configuração da porta lá FastEthernet 0/0 para inserir o IP da default-route a do gateway.
   - primeiro o comando **"exit"** depois o **"interface FastEthernet 0/0"** e agora iremos inserir o nosso ip da gateway.
   - Para inserir o nosso ip da gateway, utilize o comando ip address [ip aqui] junto com a [mascarda de rede].
   - após isso o dhcp estará configurado.

3. Passo - Configurando o Servidor WEB
   - Para configurar o servidor WEB, colocaremos mais um switch ligado ao roteador, via cabo direto.
   - E o servidor WEB conectador ao Switch, via cabo direto.
   - Agora precisamos habilitar a porta FastEthernet 0/1.
   - Após habilitar a porta iremos inserir um um ip estático para essa porta. ip address [ip] [máscara de rede].
   - Precisamos configurar o Servidor WEB, colocaremos um ipv4 para ele e a default gateway que criamos anteriormente, para porta FastEthernet 0/1.
   - Agora só acessar a pagina com o ip do servidor em algum dos computadores que temos.

4. Passo - Configurando o Servidor DNS
   - Criamos mais um Servidor que será ligado também ao Switch que tem o servidor Web.
   - Iremos configurar agora o Servidor DNS, com um ipv4, máscara de rede e a default gateway para ter saida para internet. Lembre-se que esse ip é aquele da porta FastEthernet 0/1.
   - Após iremos acessar o Serviços do Servidor DNS e iremos ativar o DNS, colocaremos um nome para esse site o ip que será o do Servidor WEB.
   - Ainda precisamos configurar o DNS no roteador já que ele não tem a inteligencia para saber que estamos agora com um servidor DNS ativo.
   - Para isso acessaremos o roteador,
