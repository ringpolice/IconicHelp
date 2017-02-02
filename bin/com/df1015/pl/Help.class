package com.df1015.pl;

import org.bukkit.ChatColor;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.event.Listener;
import org.bukkit.plugin.java.JavaPlugin;

public class Help extends JavaPlugin implements Listener {
	public void onEnable() {
		getServer().getPluginManager().registerEvents(this, this);
		getLogger().info("STARTED");
		getLogger().info("By DaRignio");
		loadConfig();
		if (!getDataFolder().exists()) {
			getDataFolder().mkdir();
		}
	}

	public void showDefaultHelpMessage(CommandSender sender) {
		for (String defaulthelp : getConfig().getStringList("default-help")) {
			sender.sendMessage(color(defaulthelp).replace("{playername}", sender.getName()));
		}
	}

	public void showExtraHelpMessage1(CommandSender sender) {
		for (String defaulthelp : getConfig().getStringList("extra1-help")) {
			sender.sendMessage(color(defaulthelp).replace("{playername}", sender.getName()));
		}
	}

	public void showExtraHelpMessage2(CommandSender sender) {
		for (String defaulthelp : getConfig().getStringList("extra2-help")) {
			sender.sendMessage(color(defaulthelp).replace("{playername}", sender.getName()));
		}
	}

	public void showStaffHelpMessage1(CommandSender sender) {
		for (String staffhelp : getConfig().getStringList("staff-help-mod")) {
			sender.sendMessage(color(staffhelp).replace("{playername}", sender.getName()));
		}
	}

	public void showStaffHelpMessage2(CommandSender sender) {
		for (String staffhelp : getConfig().getStringList("staff-help-admin")) {
			sender.sendMessage(color(staffhelp).replace("{playername}", sender.getName()));
		}
	}

	public void loadConfig() {
		getConfig().options().copyDefaults(true);
		saveConfig();

	}

	public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {
		String cmd = command.getName();
		if (cmd.equalsIgnoreCase("help")) {
			// DEFAULT MESSAGE ==
			if (sender.hasPermission("ich.default") && !sender.isOp()) {
				showDefaultHelpMessage(sender);
			}
			// EXTRA-1 MESSAGE ==
			if (sender.hasPermission("ich.extra.1") && !sender.isOp()) {
				showExtraHelpMessage1(sender);
			}
			// EXTRA-2 MESSAGE ==
			if (sender.hasPermission("ich.extra.2") && !sender.isOp()) {
				showExtraHelpMessage2(sender);
			}
			// STAFF MOD MESSAGE ==
			if (sender.hasPermission("ich.staff.1") && !sender.isOp()) {
				showStaffHelpMessage1(sender);
			}
			// STAFF ADMIN MESSAGE ==
			if (sender.hasPermission("ich.staff.2") && !sender.isOp()) {
				showStaffHelpMessage2(sender);
			}
			// DEFAULT OP MESSAGE ==
			if (sender.isOp()) {
				showDefaultHelpMessage(sender);
				showExtraHelpMessage1(sender);
				showExtraHelpMessage2(sender);
				showStaffHelpMessage1(sender);
				showStaffHelpMessage2(sender);
			}
		}
		if (cmd.equalsIgnoreCase("hreload")) {
			reloadConfig();
			saveConfig();
			sender.sendMessage(color("&c[IconicHelp] Reloading &econfig.yml"));
			sender.sendMessage(color("&cReloaded!"));
		}
		return true;
	}

	public static String color(String text) {
		return ChatColor.translateAlternateColorCodes('&', text);
	}
}
