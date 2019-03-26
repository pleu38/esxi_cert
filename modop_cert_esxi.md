---
                Voici le mode opératoire pour faire un certificat SSL pour ESXI 6.7 
---

---

> Ce mode opératoire a été testé sur Widows Server 2019 ( et 2016 )

## Prérequis

- Avoir ESXI 6.7 ou plus

- Avoir un Windows Server 2016 ou 2019 (virtuel ou physique, les deux marchent) avec autorité de certification et IIS (cf. [Installation autorité de certification et installation de IIS](modop_cert_esxi.md#Installation IIS et autorité de certification))

  # 

---

## Installation IIS et autorité de certification

### Serveur Web (IIS)

1.  Dans Gestionnaire de serveur, Cliquez sur ***Ajout des roles et fonctionnalitées***

   ![Desktop\MD\Cert\image_thumb3_thumb](Desktop\MD\Cert\image_thumb3_thumb.png)

2. Sur le wizard ouvert, cliquez simplement sur `Suivant`

   ![Desktop\MD\Cert\image_thumb6_thumb](Desktop\MD\Cert\image_thumb6_thumb.png)

3. Dans ***Type d'installation*** sélectionnez `Installation de rôles ou fonctionnalités`

4. ***Sélection du Serveur***, laisser `Sélectionner un serveur du pool de serveurs` et choisissez le serveur voulu puis `Suivant`

   

5. Parmi tous les ***rôles de serveurs***, cochez `Serveur Web (IIS)` , et `Suivant`

6. Dans ***Fonctionnalités***, vérifiez que `.NET Framework 3.5 et 4.5` sont activés

   ![Desktop\MD\Cert\server-manager-windows-2016-7](Desktop\MD\Cert\server-manager-windows-2016-7.png)

7. Cliquez sur `suivant` jusqu'a ***Role Services***, si vous voulez ajouter des rôles supplémentaires, vous pouvez le faire plutard

8. Pour finir cliquez sur `Installer` et voila vous avez un serveur web.

   ---

   ### 

   ### Autorité de certification

   #### **Prérequis**

   - [ ] Avoir un serveur web ( cf. [Installation Serveur Web(IIS)](modop_cert_esxi.md#Serveur Web(IIS)) )

   - [ ] Avoir un domaine `ph.lan`

   - [ ] controleur de domaine avec **IP fixe** `srv.ph.lan`

    

   1. Dans Gestionnaire de serveur, cliquez sur ***Ajout des roles et fonctionnalitées***

      ![Desktop\MD\Cert\image_thumb3_thumb](Desktop\MD\Cert\image_thumb3_thumb.png)

   2. Sur la boite de dialogue ***Avant de commencer***, `suivant` 

      ![Desktop\MD\Cert\image_thumb6_thumb](Desktop\MD\Cert\image_thumb6_thumb.png)

   3. Dans ***Type d'installation*** sélectionnez `Installation de rôles ou fonctionnalités`

      

   4. ***Sélection du Serveur***, laisser `Sélectionner un serveur du pool de serveurs` et choisissez le serveur voulu puis `Suivant`

      

   5. Dans l'onglet ***Rôles de serveurs***, ajouter `Services de certificats Active Directory`

      

   6. Sur la nouvelle fenêtre cliquez `Ajouter des fonctionnalités` , puis `Suivant`

      

   7. Nous ajoutons pas de fontctionalités donc `Suivant`

      

   8. Dans ***AD CS***,  cliquez `Suivant` 

      

   9. Dans ***Services de rôle***, cochez `Autorité de certification` et `Inscription de l'autorité de certification via le web`

      

   10. Puis dans ***Confirmation***, `installer`

       

   11. Dans Gestionnaire de serveur, nous allons configurer les services de certificats Active directory, pour cela cliquez sur le *panneau d'avertissement*

       

   12. Sur la fenêtre ouverte, laissez les ***informations d'identifaction*** tel quel, puis `Suivant`

       

   13. Sur ***Services de rôles***, cochez les deux roles non grisés 

       

   14. Dans l'onglet ***Type d'installation***, Sélectionnez `Autorité de certification d'entreprise`

       

   15. Puis dans ***Type d'AC***, cliquez sur `Autorité de certifcation racine`

       

   16. Nous allons créer une clée privée donc on choisis `Créer une clé privée`, puis laissez le choix par défaut, une longueur de `2048` ou `4096`, et dans l'algorythme prenez `SHA256`

       

   17. Dans le ***Nom de l'AC***, précisez `le nom commun du CA`. Le `suffixe du nom unique` et l'`aperçu du nom unique` sont définits par défaut

       

   18. Choisissez une ***période de validité***, mettez `5 Années`

       

   19. Pour la ***Base de données de l'autorité de certification*** laissez le chemin par défaut, cliquez sur `Suivant`

       

   20. Voila, vous avez créer votre CA, pour finaliser cliquez sur `Configurer`

       


