# 🚓 CONTROLE DE VIATURAS (VTR) - FROTA 1ª CIA DO 1º BPTRAN

Sistema completo de gestão de frota, controle de status operacional, histórico de baixas, motivos mecânicos/elétricos, gerenciamento de rádios/placas e relatórios em tempo real.

Otimizado para rodar **24 horas por dia, 30 dias no mês na Vercel** com banco de dados centralizado em nuvem no **Firebase Realtime Database**.

---

## ⚡ Arquitetura e Funcionamento em Tempo Real

1. **Atualização Otimista Imediata (0 ms)**:
   - Ao alterar qualquer viatura (ex: de `OPERANDO` para `BAIXADA`), a interface no computador ou celular atualiza instantaneamente na tela.
   - Uma proteção local de 8 segundos impede que leituras antigas de rede causem oscilação visual ("piscar").

2. **Transmissão Bidirecional Contínua (Stream SSE / EventSource)**:
   - A gravação é enviada diretamente ao Firebase Realtime Database em milissegundos (~80 ms).
   - O Firebase distribui o evento de atualização automaticamente para todos os outros computadores e celulares conectados, sem necessidade de recarregar a página (F5).

3. **Configuração Flexível do Banco no Próprio Painel**:
   - No modal **💾 Banco de Dados**, há um campo dedicado onde o link do Firebase pode ser consultado ou alterado a qualquer momento, com teste de conexão e botão de restauração.
   - Padrão configurado: `https://controlevtr-1c1b-default-rtdb.firebaseio.com/frota_database.json`.

4. **Persistência de Sessão e Digitação Segura**:
   - A senha e o usuário autenticado são preservados no navegador (`localStorage`), evitando solicitações repetidas de senha a cada clique.
   - As rotinas de sincronização em segundo plano protegem os campos de formulários e senhas abertos para que nada seja apagado durante a digitação.

---

## 🚀 Como Publicar via GitHub e Vercel

1. Suba este repositório para o seu **GitHub**:
   ```bash
   git add .
   git commit -m "Deploy Vercel com Firebase Realtime Database"
   git push
   ```

2. Na **Vercel** ([vercel.com](https://vercel.com)):
   - Clique em **Add New...** ➔ **Project**.
   - Selecione o repositório do GitHub.
   - Deixe o Framework Preset como **Other** e clique em **Deploy**.
   - O sistema estará ativo 24/7 de forma contínua e sem limite de horas mensais.

---

## 🛡️ Gestão de Usuários e Permissões

- O sistema inicia em modo de visualização.
- Usuários autorizados e Administrador Geral podem acessar o painel de **Usuários e Permissões** para definir permissões setor a setor através de marcações.
