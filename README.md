local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Tubers Hub | made by Shelby", "Sentinel")

-- Aba Home
local Home = Window:NewTab("Home")
local HomeSection = Home:NewSection("Home")

HomeSection:NewLabel("Welcome, User!")
HomeSection:NewLabel("This script made by Shelby")
HomeSection:NewLabel("version 1.7")

-- Variável para armazenar a GUI principal
local mainGui = game.CoreGui:FindFirstChild("KavoUI") -- Encontra a interface

-- Botão para minimizar
HomeSection:NewButton("Minimize", "Hides the GUI", function()
    if mainGui then
        mainGui.Enabled = false -- Oculta a interface
    end
end)

-- Atalho para minimizar/restaurar a GUI pressionando "M"
game:GetService("UserInputService").InputBegan:Connect(function(input, processed)
    if processed then return end
    if input.KeyCode == Enum.KeyCode.M then
        if mainGui then
            mainGui.Enabled = not mainGui.Enabled -- Alterna entre visível/invisível
        end
    end
end)

-- Aba Player
local Player = Window:NewTab("Player")
local PlayerSection = Player:NewSection("Player")

PlayerSection:NewSlider("Walkspeed", "Changes the walkspeed", 250, 16, function(s)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)

PlayerSection:NewSlider("Jumppower", "Changes the jumppower", 250, 50, function(j)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = j
end)

PlayerSection:NewButton("Inf Jumps", "Enables Inf Jumps", function()
    local InfiniteJumpEnabled = true
    game:GetService("UserInputService").JumpRequest:connect(function()
        if InfiniteJumpEnabled then
            game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end
    end)
end)
